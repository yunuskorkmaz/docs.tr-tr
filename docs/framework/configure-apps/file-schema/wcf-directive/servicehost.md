---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: fdd6d83836c4ef31a4d7c8e68cb0cc050ac6bea4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "76787797"
---
# <a name="servicehost"></a><span data-ttu-id="b07d2-101">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="b07d2-101">\@ServiceHost</span></span>

<span data-ttu-id="b07d2-102">Barındırılan hizmet ile hizmet ana bilgisayarını oluşturmak için kullanılan fabrikası ve. svc dosyasında belirtilen barındırma koduna erişmek veya derlemek için gereken diğer programlama yönlerini ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="b07d2-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>

## <a name="syntax"></a><span data-ttu-id="b07d2-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b07d2-103">Syntax</span></span>

```xml
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```

## <a name="attributes"></a><span data-ttu-id="b07d2-104">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b07d2-104">Attributes</span></span>

### <a name="service"></a><span data-ttu-id="b07d2-105">Hizmet</span><span class="sxs-lookup"><span data-stu-id="b07d2-105">Service</span></span>

<span data-ttu-id="b07d2-106">Barındırılan hizmetin CLR türü adı.</span><span class="sxs-lookup"><span data-stu-id="b07d2-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="b07d2-107">Bu, bir veya daha fazla hizmet kişilerini uygulayan bir türün tam adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b07d2-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>

### <a name="factory"></a><span data-ttu-id="b07d2-108">Fabrika</span><span class="sxs-lookup"><span data-stu-id="b07d2-108">Factory</span></span>

<span data-ttu-id="b07d2-109">Hizmet ana bilgisayarının örneğini oluşturmak için kullanılan hizmet ana bilgisayar fabrikasının CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="b07d2-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="b07d2-110">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b07d2-110">This attribute is optional.</span></span> <span data-ttu-id="b07d2-111">Belirtilmemişse, varsayılan olarak <xref:System.ServiceModel.Activation.ServiceHostFactory> kullanılır ve bir örneği döndürür <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="b07d2-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

### <a name="debug"></a><span data-ttu-id="b07d2-112">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="b07d2-112">Debug</span></span>

<span data-ttu-id="b07d2-113">Windows Communication Foundation (WCF) hizmetinin hata ayıklama sembolleriyle derlenmesi gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b07d2-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="b07d2-114">`true`WCF hizmeti hata ayıklama sembolleri ile derlenmelidir; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="b07d2-114">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>

### <a name="language"></a><span data-ttu-id="b07d2-115">Dil</span><span class="sxs-lookup"><span data-stu-id="b07d2-115">Language</span></span>

<span data-ttu-id="b07d2-116">Dosya (. svc) içindeki tüm satır içi kodları derlerken kullanılan dili belirtir.</span><span class="sxs-lookup"><span data-stu-id="b07d2-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="b07d2-117">Değerler herhangi birini temsil edebilir. `C#` `VB` `JS` Sırasıyla C#, Visual Basic ve JScript .net 'e başvuran, ve dahIl olmak üzere net destekli dil.</span><span class="sxs-lookup"><span data-stu-id="b07d2-117">The values can represent any .NET-supported language, including `C#`, `VB`, and `JS`, which refer to C#, Visual Basic, and JScript .NET, respectively.</span></span> <span data-ttu-id="b07d2-118">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b07d2-118">This attribute is optional.</span></span>

### <a name="codebehind"></a><span data-ttu-id="b07d2-119">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="b07d2-119">CodeBehind</span></span>

<span data-ttu-id="b07d2-120">XML Web hizmetini uygulayan sınıf aynı dosyada yer almıyor ve bir derlemeye derlenmediği ve *\Bin* dizinine YERLEŞTIRILEBILECEK olan XML Web hizmetini uygulayan kaynak dosyayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b07d2-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the *\Bin* directory.</span></span>

## <a name="remarks"></a><span data-ttu-id="b07d2-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b07d2-121">Remarks</span></span>

<span data-ttu-id="b07d2-122"><xref:System.ServiceModel.ServiceHost>Hizmeti barındırmak için kullanılan, Windows Communication Foundation (WCF) programlama modeli içindeki bir genişletilebilirlik noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="b07d2-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="b07d2-123">Bir fabrika deseninin, <xref:System.ServiceModel.ServiceHost> büyük olasılıkla barındırma ortamının doğrudan örneği bulunmayan çok biçimli bir tür olduğu için örneğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b07d2-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>

<span data-ttu-id="b07d2-124">Varsayılan uygulama, <xref:System.ServiceModel.Activation.ServiceHostFactory> örneği oluşturmak için kullanır <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="b07d2-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="b07d2-125">Ancak, yönergede fabrika uygulamanızın CLR türü adını belirterek kendi fabrikanızı (türetilmiş ana bilgisayarınızı döndüren bir tane) sağlayabilirsiniz `@ServiceHost` .</span><span class="sxs-lookup"><span data-stu-id="b07d2-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the `@ServiceHost` directive.</span></span>

<span data-ttu-id="b07d2-126">Varsayılan fabrika yerine kendi özel hizmet ana bilgisayar fabrikasını kullanmak için, yönergede tür adını `@ServiceHost` aşağıdaki gibi belirtmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="b07d2-126">To use you own custom service host factory instead of the default factory, just provide the type name in the `@ServiceHost` directive as follows.</span></span>

```xml
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>
```

<span data-ttu-id="b07d2-127">Fabrika uygulamalarını mümkün olduğunca ışık olarak tutun.</span><span class="sxs-lookup"><span data-stu-id="b07d2-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="b07d2-128">Çok sayıda özel mantığa sahipseniz, bu mantığı fabrika yerine ana bilgisayarınıza yerleştirirseniz, kodunuz daha yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b07d2-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>

<span data-ttu-id="b07d2-129">Örneğin, için AJAX özellikli bir uç noktasını etkinleştirmek üzere, `MyService` <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> `Factory` <xref:System.ServiceModel.Activation.ServiceHostFactory> `@ServiceHost` Aşağıdaki örnekte gösterildiği gibi, varsayılan değer yerine, öznitelik için değerini belirtin:</span><span class="sxs-lookup"><span data-stu-id="b07d2-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the `@ServiceHost` directive as shown in the following example:</span></span>

```xml
<% @ServiceHost
Service="MyService"
Language="C#"
Debug="true"
Factory="WebScriptServiceHostFactory"
%>
```

## <a name="see-also"></a><span data-ttu-id="b07d2-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b07d2-130">See also</span></span>

- [<span data-ttu-id="b07d2-131">Özel Hizmet Ana Bilgisayarı</span><span class="sxs-lookup"><span data-stu-id="b07d2-131">Custom Service Host</span></span>](../../../wcf/samples/custom-service-host.md)
