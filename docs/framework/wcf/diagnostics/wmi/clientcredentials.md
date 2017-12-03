---
title: ClientCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55f7ef12f67bd719f72f158a1fca6f120b4f448a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="clientcredentials"></a>ClientCredentials
ClientCredentials  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 ClientCredentials sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 ClientCredentials sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="clientcertificate"></a>ClientCertificate  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 X.509 sertifikası istemci, bir hizmetin kimliğini kullanır.  
  
### <a name="httpdigest"></a>HttpDigest  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Geçerli Http Digest kimlik bilgileri.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Uç noktası adresi ve yerel güvenlik belirteci hizmeti ile iletişim kurmada kullanılan bağlama.  
  
### <a name="peer"></a>Eş  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Eş düğüm kafes içindeki diğer düğümlere kendi kimliğini doğrulamak için kullandığı kimlik bilgileri.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Hizmetin X.509 sertifikası.  
  
### <a name="supportinteractive"></a>SupportInteractive  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Kimlik bilgisi etkileşimli anlaşmayı destekleyip desteklemediğini belirten bir Boole değeri.  
  
### <a name="username"></a>UserName  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Kullanıcı adı ve parola istemci hizmete kendi kimliğini doğrulamak için kullanır.  
  
### <a name="windows"></a>Windows  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Windows kimlik bilgileri hizmete kendi kimliğini doğrulamak için istemci kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ClientCredentials>
