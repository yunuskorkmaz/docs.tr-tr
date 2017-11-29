---
title: ServiceCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e4cc9d7d7d46157b7df202c6daffb31b90fa98c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="servicecredentials"></a>ServiceCredentials
ServiceCredentials  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 ServiceCredentials sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 ServiceCredentials sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="clientcertificate"></a>ClientCertificate  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Sertifika kimlik doğrulaması ve sağlama için istemci ayarlarını bu hizmet.  
  
### <a name="issuedtokenauthentication"></a>IssuedTokenAuthentication  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Geçerli belirteç kimlik doğrulama ayarlarını bu hizmet için verilmiş.  
  
### <a name="peer"></a>Eş  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Geçerli kimlik doğrulama ve eş aktarım uç noktaları tarafından kullanılacak ayarları sağlama kimlik bilgileri.  
  
### <a name="secureconversationauthentication"></a>Servicecredential  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Geçerli güvenli konuşma ayarlarını belirtir.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bu hizmet ile ilişkili sertifika.  
  
### <a name="usernameauthentication"></a>UserNameAuthentication  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bu hizmet için kullanıcı adı/parola ayarları.  
  
### <a name="windowsauthentication"></a>WindowsAuthentication  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bu hizmet Windows kimlik doğrulama ayarları.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceCredentials>
