# Hi there, I'm Nadib Rana 👋

## About Me
I'm a passionate developer with a love for coding and technology. I enjoy learning new things and building projects that solve real-world problems. 

- 🌱 I’m currently learning advanced JavaScript and exploring AI/ML technologies.
- 👯 I’m looking to collaborate on open source projects.
- 🤔 I’m looking for help with cloud computing.
- 💬 Ask me about web development, JavaScript, and Python.
- 📫 How to reach me: [Email](mailto:codecrafersnadib@gmail.com)
- ⚡ Fun fact: I love to play chess and solve puzzles.

## GitHub Stats
![Nadib's GitHub Stats](https://github-readme-stats.vercel.app/api?username=Nadib-Rana&show_icons=true&theme=radical)


## Languages and Tools

![JavaScript](https://img.shields.io/badge/-JavaScript-black?style=flat-square&logo=javascript)
![Python](https://img.shields.io/badge/-Python-black?style=flat-square&logo=python)
![C](https://img.shields.io/badge/-C-black?style=flat-square&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/-C%2B%2B-black?style=flat-square&logo=cplusplus&logoColor=white)
![HTML5](https://img.shields.io/badge/-HTML-black?style=flat-square&logo=html5)
![CSS3](https://img.shields.io/badge/-CSS-black?style=flat-square&logo=css3)
![React](https://img.shields.io/badge/-React-black?style=flat-square&logo=react)
![Node.js](https://img.shields.io/badge/-Node.js-black?style=flat-square&logo=node.js)
![MySQL](https://img.shields.io/badge/-MySQL-black?style=flat-square&logo=mysql)
![MongoDB](https://img.shields.io/badge/-MongoDB-black?style=flat-square&logo=mongodb)
![GitHub](https://img.shields.io/badge/-GitHub-black?style=flat-square&logo=github)


import React, { useState } from 'react';
import { 
  Box,
  Typography,
  Grid,
  TextField,
  Button,
  IconButton,
  Paper,
  AppBar,
  Toolbar,
  InputAdornment,
  Table,
  TableBody,
  TableCell,
  TableContainer,
  TableHead,
  TableRow,
  Avatar
} from '@mui/material';
import { 
  Search, 
  Add, 
  FilterList, 
  MoreVert, 
  Email, 
  Phone, 
  PersonAdd 
} from '@mui/icons-material';

const CRMSection = () => {
  const [showAddModal, setShowAddModal] = useState(false);
  const [searchQuery, setSearchQuery] = useState('');

  // Mock data
  const contacts = [
    { id: 1, name: 'John Doe', email: 'john@example.com', phone: '+1 234 567 890', status: 'Lead', lastContact: '2 days ago' },
    { id: 2, name: 'Jane Smith', email: 'jane@example.com', phone: '+1 345 678 901', status: 'Customer', lastContact: '1 week ago' },
    // Add more mock data...
  ];

  return (
    <Box sx={{ flexGrow: 1, p: 3 }}>
      {/* Header */}
      <AppBar position="static" color="inherit" elevation={0}>
        <Toolbar>
          <Typography variant="h6" sx={{ flexGrow: 1 }}>
            Customer Relationship Management
          </Typography>
          
          <TextField
            variant="outlined"
            size="small"
            placeholder="Search contacts..."
            InputProps={{
              startAdornment: (
                <InputAdornment position="start">
                  <Search />
                </InputAdornment>
              ),
            }}
            sx={{ mr: 2, width: 300 }}
            onChange={(e) => setSearchQuery(e.target.value)}
          />

          <Button 
            variant="contained" 
            startIcon={<Add />}
            onClick={() => setShowAddModal(true)}
          >
            Add Contact
          </Button>
        </Toolbar>
      </AppBar>

      {/* Main Content */}
      <Grid container spacing={3} sx={{ mt: 2 }}>
        {/* Left Sidebar */}
        <Grid item xs={12} md={3}>
          <Paper elevation={0} sx={{ p: 2, borderRadius: 2 }}>
            <Typography variant="subtitle1" gutterBottom>
              Quick Actions
            </Typography>
            <Button 
              fullWidth 
              variant="outlined" 
              startIcon={<Email />}
              sx={{ mb: 1 }}
            >
              Send Bulk Email
            </Button>
            <Button 
              fullWidth 
              variant="outlined" 
              startIcon={<PersonAdd />}
              sx={{ mb: 1 }}
            >
              Import Contacts
            </Button>
            <Button 
              fullWidth 
              variant="outlined" 
              startIcon={<FilterList />}
            >
              Advanced Filters
            </Button>
          </Paper>
        </Grid>

        {/* Main Table */}
        <Grid item xs={12} md={9}>
          <TableContainer component={Paper} elevation={0}>
            <Table>
              <TableHead>
                <TableRow>
                  <TableCell>Contact</TableCell>
                  <TableCell>Email</TableCell>
                  <TableCell>Phone</TableCell>
                  <TableCell>Status</TableCell>
                  <TableCell>Last Contact</TableCell>
                  <TableCell>Actions</TableCell>
                </TableRow>
              </TableHead>
              <TableBody>
                {contacts.map((contact) => (
                  <TableRow key={contact.id}>
                    <TableCell>
                      <Box sx={{ display: 'flex', alignItems: 'center' }}>
                        <Avatar sx={{ mr: 2 }}>{contact.name[0]}</Avatar>
                        {contact.name}
                      </Box>
                    </TableCell>
                    <TableCell>{contact.email}</TableCell>
                    <TableCell>{contact.phone}</TableCell>
                    <TableCell>
                      <Box 
                        sx={{ 
                          display: 'inline-block',
                          px: 1,
                          borderRadius: 1,
                          backgroundColor: 
                            contact.status === 'Lead' ? '#e3f2fd' : 
                            contact.status === 'Customer' ? '#e8f5e9' : '#f5f5f5'
                        }}
                      >
                        {contact.status}
                      </Box>
                    </TableCell>
                    <TableCell>{contact.lastContact}</TableCell>
                    <TableCell>
                      <IconButton>
                        <MoreVert />
                      </IconButton>
                    </TableCell>
                  </TableRow>
                ))}
              </TableBody>
            </Table>
          </TableContainer>
        </Grid>
      </Grid>

      {/* Add Contact Modal */}
      {showAddModal && (
        <Box sx={{ 
          position: 'fixed', 
          top: 0, 
          left: 0, 
          right: 0, 
          bottom: 0, 
          backgroundColor: 'rgba(0,0,0,0.5)',
          display: 'flex',
          alignItems: 'center',
          justifyContent: 'center'
        }}>
          <Paper sx={{ p: 3, width: 400 }}>
            <Typography variant="h6" gutterBottom>
              Add New Contact
            </Typography>
            <TextField
              fullWidth
              label="Full Name"
              margin="normal"
            />
            <TextField
              fullWidth
              label="Email"
              margin="normal"
            />
            <TextField
              fullWidth
              label="Phone"
              margin="normal"
            />
            <Box sx={{ mt: 2, display: 'flex', justifyContent: 'flex-end' }}>
              <Button 
                sx={{ mr: 2 }} 
                onClick={() => setShowAddModal(false)}
              >
                Cancel
              </Button>
              <Button variant="contained">
                Save Contact
              </Button>
            </Box>
          </Paper>
        </Box>
      )}
    </Box>
  );
};

export default CRMSection;

## Projects
Here are some of my notable projects:

- [Project 1](https://github.com/Nadib-Rana/project1) - A brief description of what this project does.
- [Project 2](https://github.com/Nadib-Rana/project2) - A brief description of what this project does.

## Get in Touch
- [LinkedIn](https://www.linkedin.com/in/your-linkedin-profile)
- [Twitter](https://twitter.com/your-twitter-profile)

Thanks for visiting my profile! Have a great day! 😄
