---
title: Azure Active Directory
description: Azure için Cloud Native .NET uygulamaları tasarlama | Azure Active Directory
ms.date: 06/30/2019
ms.openlocfilehash: 03f5ea8e84bc3c4a2a88a63d4b109aabf0c64f36
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614285"
---
# <a name="azure-active-directory"></a>Azure Active Directory

Microsoft Azure Active Directory (Azure AD), hizmet olarak kimlik ve erişim yönetimi sağlar. Müşteriler, kullanıcıların kim olduğunu, kendileri hakkında hangi bilgilerin depolanacağını, bu bilgilere kimlerin erişebileceğini, kimin yönetebileceğini ve hangi uygulamalara erişebileceğini yapılandırmak ve bakımını yapmak için kullanır. AAD, bir çoklu oturum açma (SSO) deneyimi sunarak, bu kullanıcı tarafından kullanılmak üzere yapılandırılmış uygulamalar için kimlik doğrulaması yapabilir. Bu, kendi başına kullanılabilir veya şirket içinde çalışan Windows AD ile tümleştirilebilir.

Azure AD, bulut için oluşturulmuştur. Bu, LDAP kullanan Windows AD 'nin aksine, sorgular için REST tabanlı Graph API ve OData söz dizimini kullanan, gerçek bir bulut Yerel kimlik çözümüdür. Şirket içi Active Directory, kimlik eşitleme hizmetleri 'ni kullanarak Kullanıcı özniteliklerini buluta eşitleyebilir ve Azure AD kullanarak tüm kimlik doğrulamanın bulutta yer geçirmesine olanak tanır. Alternatif olarak, kimlik doğrulaması, şirket içi Windows AD tarafından tamamlanmak üzere ADFS aracılığıyla yerel Active Directory geri dönmek için Bağlan aracılığıyla yapılandırılabilir.

Azure AD, şirket markalı oturum açma ekranlarını, çok fabrika kimlik doğrulamasını ve şirket içinde barındırılan uygulamalar için SSO sağlamak üzere kullanılan bulut tabanlı uygulama proxy 'lerini destekler. Farklı türlerde güvenlik raporlama ve uyarı özellikleri sunar.

## <a name="references"></a>Başvurular

- [Microsoft kimlik platformu](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
>[Önceki](authentication-authorization.md) 
> [Sonraki](identity-server.md)
