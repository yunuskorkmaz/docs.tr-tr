---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: c3adc675bb6c1e9011459a88fd7dc8e8cf63a880
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226592"
---
# <a name="clientcredentials"></a>ClientCredentials
ClientCredentials  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 ClientCredentials sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 ClientCredentials sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="clientcertificate"></a>ClientCertificate  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Hizmetinde kimlik doğrulaması için istemci X.509 sertifikası kullanır.  
  
### <a name="httpdigest"></a>HttpDigest  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Geçerli Http Digest kimlik bilgisi.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Yerel güvenlik belirteci hizmeti ile iletişim kurmada kullanılan bağlama ve uç nokta adresi.  
  
### <a name="peer"></a>Eş  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Eşdüzey düğümündeki diğer düğümlere kafes kendi kimliğini doğrulamak için kullandığı kimlik bilgileri.  
  
### <a name="servicecertificate"></a>serviceCertificate  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Hizmetin X.509 sertifikası.  
  
### <a name="supportinteractive"></a>SupportInteractive  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Kimlik bilgisi etkileşimli anlaşma destekleyip desteklemediğini belirten bir Boole değeri.  
  
### <a name="username"></a>UserName  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Kullanıcı adı ve parola İstemcinin hizmete kendi kimliğini doğrulamak için kullanır.  
  
### <a name="windows"></a>Windows  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Windows kimlik bilgileri hizmete kendi kimliğini doğrulamak için istemci kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ClientCredentials>
