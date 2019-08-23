---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: a56fb1bb9395425222347914fe3f4c17f1a451b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920332"
---
# <a name="servicehost"></a>\@ServiceHost
Barındırılan hizmet ile hizmet ana bilgisayarını oluşturmak için kullanılan fabrikası ve. svc dosyasında belirtilen barındırma koduna erişmek veya derlemek için gereken diğer programlama yönlerini ilişkilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a>Öznitelikler  
  
#### <a name="service"></a>Hizmet  
 Barındırılan hizmetin CLR türü adı. Bu, bir veya daha fazla hizmet kişilerini uygulayan bir türün tam adı olmalıdır.  
  
#### <a name="factory"></a>Çar  
 Hizmet ana bilgisayarının örneğini oluşturmak için kullanılan hizmet ana bilgisayar fabrikasının CLR tür adı. Bu öznitelik isteğe bağlıdır. Belirtilmemişse, varsayılan <xref:System.ServiceModel.Activation.ServiceHostFactory> olarak kullanılır ve bir <xref:System.ServiceModel.ServiceHost>örneği döndürür.  
  
#### <a name="debug"></a>Hata ayıklama  
 Windows Communication Foundation (WCF) hizmetinin hata ayıklama sembolleriyle derlenmesi gerekip gerekmediğini belirtir. `true`WCF hizmeti hata ayıklama sembolleri ile derlenmelidir; Aksi takdirde `false`,.  
  
#### <a name="language"></a>Dil  
 Dosya (. svc) içindeki tüm satır içi kodları derlerken kullanılan dili belirtir. Değerler herhangi birini temsil edebilir. Sırasıyla, Visual Basic .NET ve JScript C#.net 'e C#başvuran, vb ve JS dahil net destekli dil. Bu öznitelik isteğe bağlıdır.  
  
#### <a name="codebehind"></a>CodeBehind  
 XML Web hizmetini uygulayan sınıf aynı dosyada yer almıyor ve bir derlemeye derlenmediği ve \Bin dizinine yerleştirilebilecek olan XML Web hizmetini uygulayan kaynak dosyayı belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Hizmeti <xref:System.ServiceModel.ServiceHost> barındırmak için kullanılan, Windows Communication Foundation (WCF) programlama modeli içindeki bir genişletilebilirlik noktasıdır. Bir fabrika deseninin, büyük olasılıkla barındırma ortamının <xref:System.ServiceModel.ServiceHost> doğrudan örneği bulunmayan çok biçimli bir tür olduğu için örneğini oluşturmak için kullanılır.  
  
 Varsayılan uygulama, <xref:System.ServiceModel.ServiceHost>örneği <xref:System.ServiceModel.Activation.ServiceHostFactory> oluşturmak için kullanır. Ancak, [ \@ServiceHost](servicehost.md) yönergesinde fabrika uygulamanızın clr türü adını belirterek kendi fabrikanızı (türetilmiş ana bilgisayarınızı döndüren bir tane) sağlayabilirsiniz.  
  
 Varsayılan fabrika yerine kendi özel hizmet ana bilgisayar fabrikasını kullanmak için, [@ServiceHost](servicehost.md) yönergede tür adını aşağıdaki gibi belirtmeniz yeterlidir:  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Fabrika uygulamalarını mümkün olduğunca ışık olarak tutun. Çok sayıda özel mantığa sahipseniz, bu mantığı fabrika yerine ana bilgisayarınıza yerleştirirseniz, kodunuz daha yeniden kullanılabilir.  
  
 `MyService`Örneğin, için AJAX özellikli bir uç noktasını etkinleştirmek üzere, aşağıdaki örnekte gösterildiği <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> gibi, varsayılan <xref:System.ServiceModel.Activation.ServiceHostFactory> [@ServiceHost](servicehost.md) değer yerine `Factory` , öznitelik için değerini belirtin.  
  
## <a name="example"></a>Örnek  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Hizmet Konağı](../../../wcf/samples/custom-service-host.md)
