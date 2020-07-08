---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: cb425d9f4dadd97e93946a2b4cd9d059ea8504ce
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051369"
---
# <a name="servicehost"></a>\@ServiceHost

Barındırılan hizmet ile hizmet ana bilgisayarını oluşturmak için kullanılan fabrikası ve. svc dosyasında belirtilen barındırma koduna erişmek veya derlemek için gereken diğer programlama yönlerini ilişkilendirir.

## <a name="syntax"></a>Syntax

```aspx-csharp
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```

## <a name="attributes"></a>Öznitelikler

### <a name="service"></a>Hizmet

Barındırılan hizmetin CLR türü adı. Bu, bir veya daha fazla hizmet kişilerini uygulayan bir türün tam adı olmalıdır.

### <a name="factory"></a>Fabrika

Hizmet ana bilgisayarının örneğini oluşturmak için kullanılan hizmet ana bilgisayar fabrikasının CLR tür adı. Bu öznitelik isteğe bağlıdır. Belirtilmemişse, varsayılan olarak <xref:System.ServiceModel.Activation.ServiceHostFactory> kullanılır ve bir örneği döndürür <xref:System.ServiceModel.ServiceHost> .

### <a name="debug"></a>Hata ayıklama

Windows Communication Foundation (WCF) hizmetinin hata ayıklama sembolleriyle derlenmesi gerekip gerekmediğini belirtir. `true`WCF hizmeti hata ayıklama sembolleri ile derlenmelidir; Aksi takdirde, `false` .

### <a name="language"></a>Dil

Dosya (. svc) içindeki tüm satır içi kodları derlerken kullanılan dili belirtir. Değerler herhangi birini temsil edebilir. `C#` `VB` `JS` Sırasıyla C#, Visual Basic ve JScript .net 'e başvuran, ve dahIl olmak üzere net destekli dil. Bu öznitelik isteğe bağlıdır.

### <a name="codebehind"></a>CodeBehind

XML Web hizmetini uygulayan sınıf aynı dosyada yer almıyor ve bir derlemeye derlenmediği ve *\Bin* dizinine YERLEŞTIRILEBILECEK olan XML Web hizmetini uygulayan kaynak dosyayı belirtir.

## <a name="remarks"></a>Açıklamalar

<xref:System.ServiceModel.ServiceHost>Hizmeti barındırmak için kullanılan, Windows Communication Foundation (WCF) programlama modeli içindeki bir genişletilebilirlik noktasıdır. Bir fabrika deseninin, <xref:System.ServiceModel.ServiceHost> büyük olasılıkla barındırma ortamının doğrudan örneği bulunmayan çok biçimli bir tür olduğu için örneğini oluşturmak için kullanılır.

Varsayılan uygulama, <xref:System.ServiceModel.Activation.ServiceHostFactory> örneği oluşturmak için kullanır <xref:System.ServiceModel.ServiceHost> . Ancak, yönergede fabrika uygulamanızın CLR türü adını belirterek kendi fabrikanızı (türetilmiş ana bilgisayarınızı döndüren bir tane) sağlayabilirsiniz `@ServiceHost` .

Varsayılan fabrika yerine kendi özel hizmet ana bilgisayar fabrikasını kullanmak için, yönergede tür adını `@ServiceHost` aşağıdaki gibi belirtmeniz yeterlidir.

```xml
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>
```

Fabrika uygulamalarını mümkün olduğunca ışık olarak tutun. Çok sayıda özel mantığa sahipseniz, bu mantığı fabrika yerine ana bilgisayarınıza yerleştirirseniz, kodunuz daha yeniden kullanılabilir.

Örneğin, için AJAX özellikli bir uç noktasını etkinleştirmek üzere, `MyService` <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> `Factory` <xref:System.ServiceModel.Activation.ServiceHostFactory> `@ServiceHost` Aşağıdaki örnekte gösterildiği gibi, varsayılan değer yerine, öznitelik için değerini belirtin:

```aspx-csharp
<% @ServiceHost
Service="MyService"
Language="C#"
Debug="true"
Factory="WebScriptServiceHostFactory"
%>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Hizmet Ana Bilgisayarı](../../../wcf/samples/custom-service-host.md)
