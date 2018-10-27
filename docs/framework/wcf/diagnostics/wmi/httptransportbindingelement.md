---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 34ad4b8534d082d7f5248d42d70ca5bd0647a5dc
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454323"
---
# <a name="httptransportbindingelement"></a>HttpTransportBindingElement
HttpTransportBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 HttpTransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 HttpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="allowcookies"></a>allowCookies  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 İstemci tanımlama bilgilerini kabul eder ve bunları gelecekteki isteklerde yayar olup olmadığını belirten bir değer.  
  
### <a name="authenticationscheme"></a>AuthenticationScheme  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 HTTP dinleyicisi tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.  
  
### <a name="bypassproxyonlocal"></a>BypassProxyOnLocal  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Yerel adresler için proxy yoksayılıp sayılmayacağını belirten bir değer.  
  
### <a name="hostnamecomparisonmode"></a>hostNameComparisonMode  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirten bir değer.  
  
### <a name="keepaliveenabled"></a>keepAliveEnabled  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Etkinleştirildiğinde, HTTP bağlantıları canlı etkinlik düzeyinden bağımsız olarak tutulur.  
  
### <a name="maxbuffersize"></a>maxBufferSize  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Arabellek havuzu maksimum boyutu.  
  
### <a name="proxyaddress"></a>proxyAddress  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 HTTP istekleri için kullanılacak proxy adresini içeren bir URI.  
  
### <a name="proxyauthenticationscheme"></a>proxyAuthenticationScheme  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 HTTP proxy tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.  
  
### <a name="realm"></a>Bölge  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Kimlik doğrulaması bölgesi.  
  
### <a name="transfermode"></a>transferMode  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İletileri ara belleğe veya akışa veya bir istek belirten bir değer veya yanıt.  
  
### <a name="unsafeconnectionntlmauthentication"></a>unsafeConnectionNtlmAuthentication  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Güvensiz bağlantı paylaşımının sunucu üzerinde etkin olup olmadığını belirten bir değer.  
  
### <a name="usedefaultwebproxy"></a>useDefaultWebProxy  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Makine genelindeki proxy ayarlarının kullanıcıya özel ayarlar yerine kullanılır olup olmadığını belirten bir değer.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
