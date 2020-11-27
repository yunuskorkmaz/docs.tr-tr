---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: c63e1b3de464b306f46e2f0935b1208d7262925a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274198"
---
# <a name="clientcredentials"></a>ClientCredentials

ClientCredentials  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 ClientCredentials sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 ClientCredentials sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="clientcertificate"></a>ClientCertificate  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 İstemcinin hizmet kimliğini doğrulamak için kullandığı X. 509.440 sertifikası.  
  
### <a name="httpdigest"></a>HttpDigest  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Geçerli http Digest kimlik bilgileri.  
  
### <a name="issuedtoken"></a>IssuedToken  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Yerel güvenlik belirteci hizmetiyle iletişim kurmak için kullanılan uç nokta adresi ve bağlama.  
  
### <a name="peer"></a>Eşdüzey hizmet sağlayıcı  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Eş düğümün, ağ üzerindeki diğer düğümlere kimliğini doğrulamak için kullandığı kimlik bilgileri.  
  
### <a name="servicecertificate"></a>ServiceCertificate  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Hizmetin X. 509.440 sertifikası.  
  
### <a name="supportinteractive"></a>Supportınteractıve  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Kimlik bilgisinin etkileşimli anlaşmayı destekleyip desteklemediğini belirten bir Boole değeri.  
  
### <a name="username"></a>UserName  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı Kullanıcı adı ve parola.  
  
### <a name="windows"></a>Windows  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı Windows kimlik bilgileri.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ClientCredentials>
