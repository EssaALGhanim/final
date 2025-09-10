# Fawid
**Version:** 1.0  
**Developers:** Hatem Alawwad - ESSA ALGHANIM - ABDULLAH ALESSA

---

## Overview
**Fawid** is a digital platform that streamlines buying and selling for **cars** and **real estate** in Saudi Arabia.  
It combines structured listings, **AI-assisted negotiation**, secure **payments**, and **document automation**—with multi-channel notifications—so deals close faster and with more trust.

---

## Goals
- Enable fair, fast negotiations powered by AI.  
- Provide transparent, documented transactions invoices.  
- Offer robust discovery and search for cars & properties.  
- Build user trust with verified payments and clear post-deal steps (ratings/reviews).

---

## Features
### Listings
- Create & manage **car** and **real estate** listings.  
- Rich search with pagination & sorting.

### Negotiations & AI
- Buyer ↔ Seller negotiation threads with message history.  
- AI buyer-agent responses (concise Saudi tone).  
- Arabic summaries, bullet gists, and action items from transcripts.

### Payments & Documents
- Moyasar credit card flow with 3-D Secure and callbacks.  
- Auto-generate PDF **contracts/invoices** via Adobe API.  
- Store payment IDs/status and link to deals.

### Notifications
- WhatsApp messages for updates, receipts and OTP.  
- Call logs call summaries.

### Subscriptions & Ratings
- Plans with feature flags.  
- Post-deal ratings & reviews.

---
# API Endpoints Schedule

## Abdullah's Endpoints

### Buyer Controller (`/api/v1/buyer`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| PUT | `/update` | Update buyer profile | Abdullah |
| POST | `/register/request-otp` | Request OTP for buyer registration | Abdullah |
| POST | `/register/confirm-otp` | Confirm OTP to complete buyer registration | Abdullah |
| GET | `/filter` | Filter/search listings for the buyer | Abdullah |

### Seller Controller (`/api/v1/seller`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| PUT | `/update` | Update seller profile | Abdullah |
| POST | `/register/request-otp` | Request OTP for seller registration | Abdullah |
| POST | `/register/confirm-otp` | Confirm OTP for seller registration | Abdullah |
| GET | `/{sellerId}/listings/filter` | Get the seller's listings using filters | Abdullah |
| GET | `/negotiations/stats` | Get summary stats for the seller's negotiations | Abdullah |

### User Controller (`/api/v1/user`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| GET | `/get-all` | List all users | Abdullah |
| GET | `/get-user-by-id/{id}` | Get a single user by ID | Abdullah |
| DELETE | `/delete/{id}` | Delete a user by ID | Abdullah |
| GET | `/get-all-dto` | List users (DTO projection) | Abdullah |
| GET | `/sellers` | List sellers (DTO projection) | Abdullah |
| GET | `/buyers` | List buyers (DTO projection) | Abdullah |
| PUT | `/block-user/{userId}` | Block a user | Abdullah |
| GET | `/get-blocked-users` | List blocked users | Abdullah |
| PUT | `/active-user/{userId}` | Activate/unblock a user | Abdullah |

### Subscription Controller (`/api/v1/subscription`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| GET | `/get-all` | List subscription plans/user subscriptions | Abdullah |
| GET | `/get-by-id/{id}` | Get a subscription by ID | Abdullah |
| POST | `/monthly` | Start monthly subscription (after payment) | Abdullah |
| POST | `/yearly` | Start yearly subscription (after payment) | Abdullah |
| POST | `/cancel/{subscriptionId}` | Cancel a subscription | Abdullah |
| PUT | `/set-phone-id/{subscriptionId}/{phoneId}` | Attach a device/phone ID to a subscription | Abdullah |

---

## My Endpoints

### Car Listing Controller (`/api/v1/car-listing`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| GET | `/get/all` | Get all car listings | Essa |
| POST | `/list` | Create a new car listing | Essa |

### Real Estate Listing Controller (`/api/v1/real-estate-listing`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| GET | `/get/all` | Get all real-estate listings | Essa |
| POST | `/list` | Create a new real-estate listing | Essa |

### Listing Controller (`/api/v1/listing`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| GET | `/get/all` | Get all listings (cars + real estate) | Essa |
| GET | `/seller` | Get listings for the current seller | Essa |
| GET | `/status/{status}` | Filter listings by status | Essa |
| GET | `/type/{type}` | Filter listings by type/subtype | Essa |
| GET | `/search` | Search listings by query | Essa |
| GET | `/get-by-id/{id}` | Get a listing by ID | Essa |
| DELETE | `/delete/{id}` | Delete a listing by ID | Essa |

### Search Controller (`/api/v1/search`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| POST | `/create-car-search/{buyerId}` | Save a car search for a buyer | Essa |
| POST | `/create-real-estate-search/{buyerId}` | Save a real-estate search for a buyer | Essa |
| GET | `/get-results/{searchId}` | Get results for a saved search | Essa |

### Call Log Controller (`/api/v1/call`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| POST | `/sync/{sellerId}` | Sync/import call logs for a seller from external provider | Essa |
| GET | `/get-all` | List call logs | Essa |
| GET | `/get-call-by-call-id/{id}` | Get a call log by internal ID | Essa |
| GET | `/get-by-phone/{phoneNumber}` | Filter by phone number | Essa |
| GET | `/get-by-started-at/{startedAt}` | Filter by start timestamp | Essa |
| GET | `/get-by-status/{status}` | Filter by status | Essa |
| GET | `/get-by-seller/{sellerId}` | Filter by seller ID | Essa |
| GET | `/get-by-date-range` | Filter by date range | Essa |
| GET | `/get-by-seller-and-status` | Filter by seller + status | Essa |

### Rating Controller (`api/v1/rating`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| GET | `/buyer` | Ratings visible to the buyer | Essa |
| GET | `/seller` | Ratings visible to the seller | Essa |
| POST | `/buyer/seller/{sellerId}/{paymentId}` | Buyer rates a seller for a completed deal | Essa |

---

## Hatem's Endpoints

### Negotiation Controller (`/api/v1/negotiations`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| GET | `/get/{id}` | Get a negotiation by ID | Hatem |
| GET | `/get/list/{listingId}/buyer` | List negotiations | Hatem |
| POST | `/{listingId}/manual` | Start a manual negotiation for a listing | Hatem |
| POST | `/{listingId}/ai` | Start an AI-assisted negotiation for a listing | Hatem |
| POST | `/{id}/offer` | Submit an offer/counter-offer | Hatem |
| PUT | `/{id}/accept` | Accept a negotiation (lock agreed price) | Hatem |
| PUT | `/{id}/reject` | Reject/close a negotiation | Hatem |
| PUT | `/{negotiationId}/ai/enable` | Enable AI assistant for a negotiation | Hatem |
| PUT | `/{negotiationId}/ai/disable` | Disable AI assistant | Hatem |

### Negotiation Message Controller (`/api/v1/negotiation-message`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| POST | `/negotiations/{negotiationId}/messages/buyer` | Buyer posts a message | Hatem |
| POST | `/negotiations/{negotiationId}/messages/seller` | Seller posts a message | Hatem |
| GET | `/api/v1/negotiations/{negotiationId}/messages/all` | List all messages in a negotiation | Hatem |
| POST | `/{negotiationId}/ai/summarize` | AI summary of a negotiation thread | Hatem |

### Invoice Controller (`/api/v1/invoice`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| GET | `/all` | List generated invoices/contracts | Hatem |
| GET | `/{id}` | Get invoice metadata by ID | Hatem |
| GET | `/download/{id}` | Download invoice PDF | Hatem |
| POST | `/generate/{paymentId}` | Generate invoice/contract for a payment | Hatem |

### Payment Controller (`/api/v1/payment`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| GET | `/get-all` | List all payment records | Hatem |
| GET | `/get-payment-by-id/{id}` | Get a payment record by DB ID | Hatem |
| GET | `/get-payment-status/{paymentId}` | Check gateway status by payment ID | Hatem |
| POST | `/process-payment/{negotiationId}` | Create/process payment for a negotiation | Hatem |
| POST | `/process-subscription-payment/{subscriptionId}` | Process payment for a subscription plan | Hatem |
| GET | `/callback` | Handle gateway callback (status update) | Hatem |

### Contact Controller (`/api/v1/contact-us`)
| REST | Endpoint | Description | Developer |
|------|----------|-------------|-----------|
| POST | `/new` | Create new contact message | Hatem |
| GET | `/get-all` | Get all contact messages | Hatem |
| GET | `/get-by-id/{id}` | Get contact message by ID | Hatem |
| DELETE | `/delete/{messageId}` | Delete a contact message | Hatem |


## Summary
- **Total Endpoints**: 60
- **Abdullah**: 25 endpoints (User management, Buyer/Seller profiles, Subscriptions)
- **Essa**: 23 endpoints (Listings, Payments, Call logs, Search, Ratings)
- **Hatem**: 22 endpoints (Negotiations, Messages, Invoices, Payments, Contact)
---


##Tech

| Tech                  | Purpose                        |
| --------------------- | ------------------------------ |
| Java                  | Programming language           |
| Spring Boot           | Backend framework              |
| Spring Web            | Build RESTful APIs             |
| Spring Data JPA       | Database operations            |
| Spring Security       | Authentication & Authorization |
| Spring AI             | AI integration with Spring project |
| Jakarta Validation    | User input validation          |
| MySQL                 | Relational databases           |
| Lombok                | Reduce boilerplate code        |
| Maven                 | Build & dependency management  |
| JUnit                 | Unit testing                   |
| AWS                   | Cloud deployment               |
| GitHub                | Version control & collaboration |
| Moyasar               | Saudi payment gateway for secure transactions |
| Adobe Acrobat PDF API | Generate & export invoices     |
| OpenAI API            | LLM for negotiations, summaries & translations |
| VAPI                  | AI voice agent for automated phone calls |
| UltraMessage          | WhatsApp integration           |
| Postman               | API testing                    |
| Figma                 | UI/UX design                   |
| Linear                | Task management platform       | 


---

## Class Diagram

<img width="2672" height="1924" alt="Untitled (2)" src="https://github.com/user-attachments/assets/6f576bd6-32a3-4724-8b44-9ac828bc6432" />

---

## Usecase Diagram

<img width="4832" height="530" alt="final drawio" src="https://github.com/user-attachments/assets/401d538f-7745-4a63-84c5-d7670bf889ec" />


