---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: dd3dd026749ccc299cd922b79dcae8ccbcc722d8
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968822"
---
# <a name="servicehost"></a>\@ServiceHost
Barındırılan hizmet ile hizmet ana bilgisayarını oluşturmak için kullanılan fabrikası ve. svc dosyasında belirtilen barındırma koduna erişmek veya derlemek için gereken diğer programlama yönlerini ilişkilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```  
  
## <a name="attributes"></a>Öznitelikler  
  
#### <a name="service"></a>Hizmet  
 Barındırılan hizmetin CLR türü adı. Bu, bir veya daha fazla hizmet kişilerini uygulayan bir türün tam adı olmalıdır.  
  
#### <a name="factory"></a>Çar  
 Hizmet ana bilgisayarının örneğini oluşturmak için kullanılan hizmet ana bilgisayar fabrikasının CLR tür adı. Bu öznitelik isteğe bağlıdır. Belirtilmemişse, varsayılan <xref:System.ServiceModel.Activation.ServiceHostFactory> kullanılır ve bu bir <xref:System.ServiceModel.ServiceHost>örneğini döndürür.  
  
#### <a name="debug"></a>Hata ayıklama  
 Windows Communication Foundation (WCF) hizmetinin hata ayıklama sembolleriyle derlenmesi gerekip gerekmediğini belirtir. WCF hizmetinin hata ayıklama simgeleriyle derlenmesi gerekiyorsa `true`; Aksi takdirde, `false`.  
  
#### <a name="language"></a>Dil  
 Dosya (. svc) içindeki tüm satır içi kodları derlerken kullanılan dili belirtir. Değerler herhangi birini temsil edebilir. Sırasıyla, Visual Basic .NET ve JScript C#.net 'e C#başvuran, vb ve JS dahil net destekli dil. Bu öznitelik isteğe bağlıdır.  
  
#### <a name="codebehind"></a>CodeBehind  
 XML Web hizmetini uygulayan sınıf aynı dosyada yer almıyor ve bir derlemeye derlenmediği ve \Bin dizinine yerleştirilebilecek olan XML Web hizmetini uygulayan kaynak dosyayı belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Hizmeti barındırmak için kullanılan <xref:System.ServiceModel.ServiceHost>, Windows Communication Foundation (WCF) programlama modeli içindeki bir genişletilebilirlik noktasıdır. Bir fabrika deseninin, büyük olasılıkla barındırma ortamının doğrudan örneği bulunmayan çok biçimli bir tür olduğu için <xref:System.ServiceModel.ServiceHost> örneğini oluşturmak için kullanılır.  
  
 Varsayılan uygulama, <xref:System.ServiceModel.ServiceHost>örneğini oluşturmak için <xref:System.ServiceModel.Activation.ServiceHostFactory> kullanır. Ancak, [\@ServiceHost](servicehost.md) yönergesinde FABRIKA uygulamanızın clr türü adını belirterek kendi fabrikanızı (türetilmiş ana bilgisayarınızı döndüren bir tane) sağlayabilirsiniz.  
  
 Varsayılan fabrika yerine kendi özel hizmet ana bilgisayar fabrikasını kullanmak için, tür adını [@ServiceHost](servicehost.md) yönergesinde aşağıdaki gibi belirtmeniz yeterlidir:  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Fabrika uygulamalarını mümkün olduğunca ışık olarak tutun. Çok sayıda özel mantığa sahipseniz, bu mantığı fabrika yerine ana bilgisayarınıza yerleştirirseniz, kodunuz daha yeniden kullanılabilir.  
  
 Örneğin, `MyService`için AJAX özellikli bir uç noktayı etkinleştirmek üzere, aşağıdaki örnekte gösterildiği gibi, [@ServiceHost](servicehost.md) yönergesinde varsayılan <xref:System.ServiceModel.Activation.ServiceHostFactory>yerine `Factory` özniteliğinin değeri için <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> belirtin.  
  
## <a name="example"></a>Örnek  
  
```xml  
<% @ServiceHost
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Hizmet Konağı](../../../wcf/samples/custom-service-host.md)
