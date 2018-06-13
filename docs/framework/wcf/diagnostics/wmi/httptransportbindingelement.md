---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 1975fd2e04a5c9cdb68bc838802abafbd781b7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487026"
---
# <a name="httptransportbindingelement"></a>HttpTransportBindingElement
HttpTransportBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 HttpTransportBindingElement sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 HttpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="allowcookies"></a>allowCookies  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 İstemci tanımlama bilgilerini kabul eder ve sonraki isteklerde yayar olup olmadığını belirten bir değer.  
  
### <a name="authenticationscheme"></a>authenticationScheme  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bir HTTP dinleyicisi tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.  
  
### <a name="bypassproxyonlocal"></a>BypassProxyOnLocal  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Yerel adresler için proxy yoksayılır olup olmadığını belirten bir değer.  
  
### <a name="hostnamecomparisonmode"></a>hostNameComparisonMode  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer.  
  
### <a name="keepaliveenabled"></a>keepAliveEnabled  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Etkinleştirildiğinde, HTTP bağlantılarını etkinlik düzeyi bağımsız olarak Canlı tutulur.  
  
### <a name="maxbuffersize"></a>maxBufferSize  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Arabellek havuzu en büyük boyutu.  
  
### <a name="proxyaddress"></a>proxyAddress  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 HTTP istekleri için kullanılacak proxy adresi içeren bir URI.  
  
### <a name="proxyauthenticationscheme"></a>proxyAuthenticationScheme  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bir HTTP proxy'si tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.  
  
### <a name="realm"></a>Bölge  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Kimlik doğrulaması bölgesi.  
  
### <a name="transfermode"></a>transferMode  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 İletileri olup ara belleğe veya akışa veya istek belirten bir değer veya yanıt.  
  
### <a name="unsafeconnectionntlmauthentication"></a>unsafeConnectionNtlmAuthentication  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Güvenli bağlantı paylaşımı sunucu üzerinde etkin olup olmadığını belirten bir değer.  
  
### <a name="usedefaultwebproxy"></a>useDefaultWebProxy  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Makine genelinde proxy ayarlarını yerine kullanıcıya özgü ayarları kullanılıp kullanılmayacağını belirten değer.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
