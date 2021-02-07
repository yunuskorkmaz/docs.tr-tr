---
description: 'Daha fazla bilgi edinin: ServiceCredentials'
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: bfd025a8f671a3c5aea537059cde0e751cfa9bb9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715554"
---
# <a name="servicecredentials"></a>ServiceCredentials

ServiceCredentials  
  
## <a name="syntax"></a>Syntax  
  
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

 ServiceCredentials sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 ServiceCredentials sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="clientcertificate"></a>ClientCertificate  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bu hizmet için istemci sertifikası kimlik doğrulaması ve sağlama ayarları.  
  
### <a name="issuedtokenauthentication"></a>IssuedTokenAuthentication  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bu hizmet için geçerli verilen belirteç kimlik doğrulama ayarları.  
  
### <a name="peer"></a>Eşdüzey hizmet sağlayıcı  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Eş aktarım noktaları tarafından kullanılacak geçerli kimlik bilgisi kimlik doğrulaması ve sağlama ayarları.  
  
### <a name="secureconversationauthentication"></a>Servicecredential  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Geçerli güvenli konuşma ayarlarını belirtir.  
  
### <a name="servicecertificate"></a>ServiceCertificate  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bu hizmetle ilişkili sertifika.  
  
### <a name="usernameauthentication"></a>UserNameAuthentication  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bu hizmetin Kullanıcı adı/parola ayarları.  
  
### <a name="windowsauthentication"></a>WindowsAuthentication  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bu hizmet için Windows kimlik doğrulama ayarları.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceCredentials>
