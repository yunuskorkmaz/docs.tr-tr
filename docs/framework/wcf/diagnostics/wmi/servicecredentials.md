---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: d9563bd3bfe067ad83bfa03e7c6375a9db933f14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230934"
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceCredentials>
