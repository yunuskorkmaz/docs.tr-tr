---
description: 'Daha fazla bilgi edinin: HttpTransportBindingElement'
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 6c516dd7124d52828145787d55421d12031c2d36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757377"
---
# <a name="httptransportbindingelement"></a>HttpTransportBindingElement

HttpTransportBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 HttpTransportBindingElement sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 HttpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="allowcookies"></a>AllowCookies  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir değer.  
  
### <a name="authenticationscheme"></a>AuthenticationScheme  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bir HTTP dinleyicisi tarafından işlenmekte olan istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.  
  
### <a name="bypassproxyonlocal"></a>BypassProxyOnLocal  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Yerel adresler için proxy 'lerin yoksayılıp yoksayılmadığını gösteren bir değer.  
  
### <a name="hostnamecomparisonmode"></a>HostNameComparisonMode  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 URI üzerinde eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer.  
  
### <a name="keepaliveenabled"></a>KeepAliveEnabled  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Etkinleştirildiğinde, etkinlik düzeyinden bağımsız olarak HTTP bağlantıları canlı tutulur.  
  
### <a name="maxbuffersize"></a>MaxBufferSize  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Arabellek havuzunun en büyük boyutu.  
  
### <a name="proxyaddress"></a>ProxyAddress  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 HTTP istekleri için kullanılacak proxy adresini içeren bir URI.  
  
### <a name="proxyauthenticationscheme"></a>ProxyAuthenticationScheme  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bir HTTP proxy tarafından işlenmekte olan istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.  
  
### <a name="realm"></a>Bölge  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Kimlik doğrulama bölgesi.  
  
### <a name="transfermode"></a>TransferMode  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 İletilerin arabelleğe alınıp alınmayacağını veya bir istek ya da yanıt olduğunu belirten bir değer.  
  
### <a name="unsafeconnectionntlmauthentication"></a>UnsafeConnectionNtlmAuthentication  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Sunucuda güvenli olmayan bağlantı paylaşımının etkin olup olmadığını gösteren bir değer.  
  
### <a name="usedefaultwebproxy"></a>UseDefaultWebProxy  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Kullanıcıya özel ayarlar yerine makine genelindeki proxy ayarlarının kullanılıp kullanılmayacağını belirten bir değer.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
