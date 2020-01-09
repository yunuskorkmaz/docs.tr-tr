---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 3c7da8d5a473b801da8c48d1cb1504b95cc6c769
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342126"
---
# <a name="servicehost"></a><span data-ttu-id="80fbc-101">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="80fbc-101">\@ServiceHost</span></span>
<span data-ttu-id="80fbc-102">Barındırılan hizmet ile hizmet ana bilgisayarını oluşturmak için kullanılan fabrikası ve. svc dosyasında belirtilen barındırma koduna erişmek veya derlemek için gereken diğer programlama yönlerini ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="80fbc-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80fbc-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80fbc-103">Syntax</span></span>  
  
```xml  
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```  
  
## <a name="attributes"></a><span data-ttu-id="80fbc-104">{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="80fbc-104">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="80fbc-105">Hizmet</span><span class="sxs-lookup"><span data-stu-id="80fbc-105">Service</span></span>  
 <span data-ttu-id="80fbc-106">Barındırılan hizmetin CLR türü adı.</span><span class="sxs-lookup"><span data-stu-id="80fbc-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="80fbc-107">Bu, bir veya daha fazla hizmet kişilerini uygulayan bir türün tam adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="80fbc-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="80fbc-108">Fabrika</span><span class="sxs-lookup"><span data-stu-id="80fbc-108">Factory</span></span>  
 <span data-ttu-id="80fbc-109">Hizmet ana bilgisayarının örneğini oluşturmak için kullanılan hizmet ana bilgisayar fabrikasının CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="80fbc-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="80fbc-110">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="80fbc-110">This attribute is optional.</span></span> <span data-ttu-id="80fbc-111">Belirtilmemişse, varsayılan <xref:System.ServiceModel.Activation.ServiceHostFactory> kullanılır ve bu bir <xref:System.ServiceModel.ServiceHost>örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="80fbc-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="80fbc-112">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="80fbc-112">Debug</span></span>  
 <span data-ttu-id="80fbc-113">Windows Communication Foundation (WCF) hizmetinin hata ayıklama sembolleriyle derlenmesi gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="80fbc-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="80fbc-114">WCF hizmetinin hata ayıklama simgeleriyle derlenmesi gerekiyorsa `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="80fbc-114">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="80fbc-115">Dil</span><span class="sxs-lookup"><span data-stu-id="80fbc-115">Language</span></span>  
 <span data-ttu-id="80fbc-116">Dosya (. svc) içindeki tüm satır içi kodları derlerken kullanılan dili belirtir.</span><span class="sxs-lookup"><span data-stu-id="80fbc-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="80fbc-117">Değerler herhangi birini temsil edebilir. Sırasıyla, Visual Basic ve JScript .NET 'e C#başvuran `C#`, `VB`ve `JS`dahil olmak üzere net destekli dil.</span><span class="sxs-lookup"><span data-stu-id="80fbc-117">The values can represent any .NET-supported language, including `C#`, `VB`, and `JS`, which refer to C#, Visual Basic, and JScript .NET, respectively.</span></span> <span data-ttu-id="80fbc-118">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="80fbc-118">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="80fbc-119">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="80fbc-119">CodeBehind</span></span>  
 <span data-ttu-id="80fbc-120">XML Web hizmetini uygulayan sınıf aynı dosyada yer almıyor ve bir derlemeye derlenmediği ve \Bin dizinine yerleştirilebilecek olan XML Web hizmetini uygulayan kaynak dosyayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="80fbc-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80fbc-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80fbc-121">Remarks</span></span>  
 <span data-ttu-id="80fbc-122">Hizmeti barındırmak için kullanılan <xref:System.ServiceModel.ServiceHost>, Windows Communication Foundation (WCF) programlama modeli içindeki bir genişletilebilirlik noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="80fbc-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="80fbc-123">Bir fabrika deseninin, büyük olasılıkla barındırma ortamının doğrudan örneği bulunmayan çok biçimli bir tür olduğu için <xref:System.ServiceModel.ServiceHost> örneğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80fbc-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="80fbc-124">Varsayılan uygulama, <xref:System.ServiceModel.ServiceHost>örneğini oluşturmak için <xref:System.ServiceModel.Activation.ServiceHostFactory> kullanır.</span><span class="sxs-lookup"><span data-stu-id="80fbc-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="80fbc-125">Ancak, [\@ServiceHost](servicehost.md) yönergesinde FABRIKA uygulamanızın clr türü adını belirterek kendi fabrikanızı (türetilmiş ana bilgisayarınızı döndüren bir tane) sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80fbc-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [\@ServiceHost](servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="80fbc-126">Varsayılan fabrika yerine kendi özel hizmet ana bilgisayar fabrikasını kullanmak için, tür adını [@ServiceHost](servicehost.md) yönergesinde aşağıdaki gibi belirtmeniz yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="80fbc-126">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="80fbc-127">Fabrika uygulamalarını mümkün olduğunca ışık olarak tutun.</span><span class="sxs-lookup"><span data-stu-id="80fbc-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="80fbc-128">Çok sayıda özel mantığa sahipseniz, bu mantığı fabrika yerine ana bilgisayarınıza yerleştirirseniz, kodunuz daha yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="80fbc-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="80fbc-129">Örneğin, `MyService`için AJAX özellikli bir uç noktayı etkinleştirmek üzere, aşağıdaki örnekte gösterildiği gibi, [@ServiceHost](servicehost.md) yönergesinde varsayılan <xref:System.ServiceModel.Activation.ServiceHostFactory>yerine `Factory` özniteliğinin değeri için <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> belirtin.</span><span class="sxs-lookup"><span data-stu-id="80fbc-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80fbc-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="80fbc-130">Example</span></span>  
  
```xml  
<% @ServiceHost
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="80fbc-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80fbc-131">See also</span></span>

- [<span data-ttu-id="80fbc-132">Özel Hizmet Konağı</span><span class="sxs-lookup"><span data-stu-id="80fbc-132">Custom Service Host</span></span>](../../../wcf/samples/custom-service-host.md)
