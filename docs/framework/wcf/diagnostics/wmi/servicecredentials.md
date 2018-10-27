---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: 26bd0c95f930bf7859ae6409d797afbb596844fa
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180673"
---
# <a name="servicecredentials"></a>ServiceCredentials
ServiceCredentials  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 ServiceCredentials sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 ServiceCredentials sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="clientcertificate"></a>ClientCertificate  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İstemci sertifikası kimlik doğrulaması ve sağlama ayarlarını bu hizmet için.  
  
### <a name="issuedtokenauthentication"></a>ServiceCredentials  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Geçerli belirteç kimlik doğrulaması ayarlarını bu hizmet için verilmiş.  
  
### <a name="peer"></a>Eş  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Geçerli kimlik doğrulama ve hazırlama ayarları eş aktarım uç noktaları tarafından kullanılmak üzere kimlik bilgileri.  
  
### <a name="secureconversationauthentication"></a>Servicecredential  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Geçerli bir güvenli konuşma ayarlarını belirtir.  
  
### <a name="servicecertificate"></a>serviceCertificate  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Bu hizmetle ilişkili sertifika.  
  
### <a name="usernameauthentication"></a>UserNameAuthentication  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Bu hizmet için kullanıcı adı/parola ayarlar.  
  
### <a name="windowsauthentication"></a>WindowsAuthentication  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Bu hizmet Windows kimlik doğrulama ayarları.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceCredentials>
