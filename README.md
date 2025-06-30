import React, { useState, useEffect } from 'react';
import { Github, Linkedin, Mail, Globe, Code, Database, BarChart3, Zap, Trophy, Star, GitBranch, Users, Eye } from 'lucide-react';

const GitHubProfile = () => {
  const [currentSkill, setCurrentSkill] = useState(0);
  const [isVisible, setIsVisible] = useState(false);
  const [mousePosition, setMousePosition] = useState({ x: 0, y: 0 });

  const skills = [
    { name: 'Python', icon: '🐍', level: 90, color: 'from-blue-500 to-green-500' },
    { name: 'Power BI', icon: '📊', level: 85, color: 'from-yellow-400 to-orange-500' },
    { name: 'SQL', icon: '🗃️', level: 88, color: 'from-blue-400 to-purple-500' },
    { name: 'Data Analysis', icon: '📈', level: 92, color: 'from-green-400 to-blue-500' },
    { name: 'Pandas', icon: '🐼', level: 87, color: 'from-purple-400 to-pink-500' },
    { name: 'Excel', icon: '📋', level: 85, color: 'from-green-500 to-teal-500' }
  ];

  const projects = [
    { name: 'Sales Dashboard', desc: 'Interactive Power BI dashboard with real-time KPIs', tech: ['Power BI', 'SQL', 'DAX'] },
    { name: 'Customer Analytics', desc: 'Python-based customer segmentation analysis', tech: ['Python', 'Pandas', 'Seaborn'] },
    { name: 'Financial Forecasting', desc: 'Time series analysis for revenue prediction', tech: ['Python', 'SQL', 'Tableau'] }
  ];

  useEffect(() => {
    setIsVisible(true);
    const interval = setInterval(() => {
      setCurrentSkill((prev) => (prev + 1) % skills.length);
    }, 3000);
    return () => clearInterval(interval);
  }, []);

  useEffect(() => {
    const handleMouseMove = (e) => {
      setMousePosition({ x: e.clientX, y: e.clientY });
    };
    window.addEventListener('mousemove', handleMouseMove);
    return () => window.removeEventListener('mousemove', handleMouseMove);
  }, []);

  return (
    <div className="min-h-screen bg-gradient-to-br from-slate-900 via-purple-900 to-slate-900 text-white relative overflow-hidden">
      {/* Animated Background */}
      <div className="absolute inset-0 overflow-hidden">
        <div className="absolute -top-4 -left-4 w-72 h-72 bg-purple-500 rounded-full mix-blend-multiply filter blur-xl opacity-20 animate-pulse"></div>
        <div className="absolute top-1/2 -right-4 w-72 h-72 bg-blue-500 rounded-full mix-blend-multiply filter blur-xl opacity-20 animate-pulse animation-delay-2000"></div>
        <div className="absolute -bottom-8 left-1/2 w-72 h-72 bg-pink-500 rounded-full mix-blend-multiply filter blur-xl opacity-20 animate-pulse animation-delay-4000"></div>
      </div>

      {/* Mouse Follower */}
      <div 
        className="fixed w-6 h-6 bg-gradient-to-r from-blue-400 to-purple-500 rounded-full pointer-events-none z-50 mix-blend-difference transition-all duration-300 ease-out"
        style={{
          left: mousePosition.x - 12,
          top: mousePosition.y - 12,
          transform: 'scale(1.2)'
        }}
      ></div>

      <div className="container mx-auto px-4 py-8 relative z-10">
        {/* Header Section */}
        <div className={`text-center mb-16 transform transition-all duration-1000 ${isVisible ? 'translate-y-0 opacity-100' : 'translate-y-10 opacity-0'}`}>
          <div className="relative inline-block mb-6">
            <div className="w-32 h-32 mx-auto rounded-full bg-gradient-to-r from-blue-500 via-purple-500 to-pink-500 p-1 animate-spin-slow">
              <div className="w-full h-full bg-slate-900 rounded-full flex items-center justify-center text-4xl font-bold">
                PK
              </div>
            </div>
            <div className="absolute -top-2 -right-2 w-8 h-8 bg-green-500 rounded-full animate-bounce"></div>
          </div>
          
          <h1 className="text-5xl font-bold mb-4 bg-gradient-to-r from-blue-400 via-purple-400 to-pink-400 bg-clip-text text-transparent">
            D Praveen Kumar
          </h1>
          
          <div className="text-xl text-gray-300 mb-6 max-w-2xl mx-auto">
            <span className="inline-block animate-pulse">🚀</span> Aspiring Data & Business Analyst
            <br />
            <span className="text-gradient bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">
              Transforming data into decisions with storytelling dashboards
            </span>
          </div>

          {/* Social Links */}
          <div className="flex justify-center space-x-4 mb-8">
            {[
              { icon: Linkedin, href: 'https://www.linkedin.com/in/praveen-kumar-869844200', color: 'from-blue-500 to-blue-600' },
              { icon: Mail, href: 'mailto:praveenkumard083@gmail.com', color: 'from-red-500 to-red-600' },
              { icon: Globe, href: '#', color: 'from-green-500 to-green-600' },
              { icon: Github, href: '#', color: 'from-gray-500 to-gray-600' }
            ].map((social, idx) => (
              <a key={idx} href={social.href} className="group relative">
                <div className={`p-3 rounded-full bg-gradient-to-r ${social.color} transform transition-all duration-300 group-hover:scale-110 group-hover:shadow-lg`}>
                  <social.icon className="w-6 h-6 text-white" />
                </div>
                <div className="absolute inset-0 rounded-full bg-white opacity-0 group-hover:opacity-20 transition-opacity duration-300"></div>
              </a>
            ))}
          </div>
        </div>

        {/* Skills Showcase */}
        <div className="mb-16">
          <h2 className="text-3xl font-bold text-center mb-8 flex items-center justify-center">
            <Zap className="mr-3 text-yellow-400" />
            Skills & Expertise
          </h2>
          
          <div className="grid md:grid-cols-2 gap-8 max-w-4xl mx-auto">
            {/* Current Skill Highlight */}
            <div className="bg-slate-800/50 backdrop-blur-sm rounded-2xl p-6 border border-slate-700/50">
              <div className="text-center mb-4">
                <div className="text-4xl mb-2">{skills[currentSkill].icon}</div>
                <h3 className="text-2xl font-bold text-white">{skills[currentSkill].name}</h3>
              </div>
              <div className="relative">
                <div className="w-full bg-slate-700 rounded-full h-3">
                  <div 
                    className={`h-3 bg-gradient-to-r ${skills[currentSkill].color} rounded-full transition-all duration-1000 ease-out relative overflow-hidden`}
                    style={{ width: `${skills[currentSkill].level}%` }}
                  >
                    <div className="absolute inset-0 bg-white/20 animate-pulse"></div>
                  </div>
                </div>
                <span className="text-sm text-gray-400 mt-2 block">{skills[currentSkill].level}% Proficiency</span>
              </div>
            </div>

            {/* Skills Grid */}
            <div className="grid grid-cols-2 gap-4">
              {skills.map((skill, idx) => (
                <div 
                  key={idx}
                  className={`p-4 rounded-xl transition-all duration-300 cursor-pointer ${
                    idx === currentSkill 
                      ? 'bg-gradient-to-r from-blue-500/20 to-purple-500/20 border-2 border-blue-400 scale-105' 
                      : 'bg-slate-800/50 border border-slate-700/50 hover:border-slate-600'
                  }`}
                  onClick={() => setCurrentSkill(idx)}
                >
                  <div className="text-2xl mb-2">{skill.icon}</div>
                  <div className="text-sm font-medium">{skill.name}</div>
                </div>
              ))}
            </div>
          </div>
        </div>

        {/* Projects Section */}
        <div className="mb-16">
          <h2 className="text-3xl font-bold text-center mb-8 flex items-center justify-center">
            <Code className="mr-3 text-blue-400" />
            Featured Projects
          </h2>
          
          <div className="grid md:grid-cols-3 gap-6 max-w-6xl mx-auto">
            {projects.map((project, idx) => (
              <div key={idx} className="group relative">
                <div className="bg-slate-800/50 backdrop-blur-sm rounded-xl p-6 border border-slate-700/50 hover:border-blue-400/50 transition-all duration-300 transform hover:-translate-y-2 hover:shadow-2xl">
                  <div className="absolute inset-0 bg-gradient-to-r from-blue-500/10 to-purple-500/10 rounded-xl opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                  
                  <h3 className="text-xl font-bold mb-3 text-white relative z-10">{project.name}</h3>
                  <p className="text-gray-300 mb-4 relative z-10">{project.desc}</p>
                  
                  <div className="flex flex-wrap gap-2 relative z-10">
                    {project.tech.map((tech, techIdx) => (
                      <span key={techIdx} className="px-3 py-1 bg-slate-700 rounded-full text-xs text-blue-300 border border-slate-600">
                        {tech}
                      </span>
                    ))}
                  </div>
                </div>
              </div>
            ))}
          </div>
        </div>

        {/* Stats Section */}
        <div className="text-center">
          <h2 className="text-3xl font-bold mb-8 flex items-center justify-center">
            <BarChart3 className="mr-3 text-green-400" />
            GitHub Analytics
          </h2>
          
          <div className="grid md:grid-cols-4 gap-6 max-w-4xl mx-auto mb-8">
            {[
              { icon: GitBranch, label: 'Repositories', value: '25+', color: 'text-blue-400' },
              { icon: Star, label: 'Stars Earned', value: '150+', color: 'text-yellow-400' },
              { icon: Users, label: 'Followers', value: '50+', color: 'text-green-400' },
              { icon: Eye, label: 'Profile Views', value: '500+', color: 'text-purple-400' }
            ].map((stat, idx) => (
              <div key={idx} className="bg-slate-800/50 backdrop-blur-sm rounded-xl p-6 border border-slate-700/50 hover:border-slate-600 transition-all duration-300">
                <stat.icon className={`w-8 h-8 mx-auto mb-3 ${stat.color}`} />
                <div className="text-2xl font-bold text-white mb-1">{stat.value}</div>
                <div className="text-gray-400 text-sm">{stat.label}</div>
              </div>
            ))}
          </div>

          {/* Call to Action */}
          <div className="bg-gradient-to-r from-blue-600 to-purple-600 rounded-2xl p-8 max-w-2xl mx-auto">
            <h3 className="text-2xl font-bold mb-4">Let's Collaborate!</h3>
            <p className="text-blue-100 mb-6">
              Open to opportunities in Data Analysis, Business Intelligence, and Analytics Engineering
            </p>
            <div className="flex justify-center space-x-4">
              <button className="bg-white text-blue-600 px-6 py-3 rounded-lg font-semibold hover:bg-blue-50 transition-colors duration-300">
                View Resume
              </button>
              <button className="border-2 border-white text-white px-6 py-3 rounded-lg font-semibold hover:bg-white hover:text-blue-600 transition-colors duration-300">
                Contact Me
              </button>
            </div>
          </div>
        </div>
      </div>

      <style jsx>{`
        @keyframes spin-slow {
          from { transform: rotate(0deg); }
          to { transform: rotate(360deg); }
        }
        .animate-spin-slow {
          animation: spin-slow 8s linear infinite;
        }
        .animation-delay-2000 {
          animation-delay: 2s;
        }
        .animation-delay-4000 {
          animation-delay: 4s;
        }
      `}</style>
    </div>
  );
};

export default GitHubProfile;
