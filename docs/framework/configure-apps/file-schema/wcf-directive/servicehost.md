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
# <a name="servicehost"></a><span data-ttu-id="e2e52-101">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="e2e52-101">\@ServiceHost</span></span>
<span data-ttu-id="e2e52-102">Barındırılan hizmet ile hizmet ana bilgisayarını oluşturmak için kullanılan fabrikası ve. svc dosyasında belirtilen barındırma koduna erişmek veya derlemek için gereken diğer programlama yönlerini ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="e2e52-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2e52-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2e52-103">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="e2e52-104">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e2e52-104">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="e2e52-105">Hizmet</span><span class="sxs-lookup"><span data-stu-id="e2e52-105">Service</span></span>  
 <span data-ttu-id="e2e52-106">Barındırılan hizmetin CLR türü adı.</span><span class="sxs-lookup"><span data-stu-id="e2e52-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="e2e52-107">Bu, bir veya daha fazla hizmet kişilerini uygulayan bir türün tam adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2e52-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="e2e52-108">Çar</span><span class="sxs-lookup"><span data-stu-id="e2e52-108">Factory</span></span>  
 <span data-ttu-id="e2e52-109">Hizmet ana bilgisayarının örneğini oluşturmak için kullanılan hizmet ana bilgisayar fabrikasının CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="e2e52-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="e2e52-110">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e2e52-110">This attribute is optional.</span></span> <span data-ttu-id="e2e52-111">Belirtilmemişse, varsayılan <xref:System.ServiceModel.Activation.ServiceHostFactory> olarak kullanılır ve bir <xref:System.ServiceModel.ServiceHost>örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="e2e52-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="e2e52-112">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e2e52-112">Debug</span></span>  
 <span data-ttu-id="e2e52-113">Windows Communication Foundation (WCF) hizmetinin hata ayıklama sembolleriyle derlenmesi gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2e52-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="e2e52-114">`true`WCF hizmeti hata ayıklama sembolleri ile derlenmelidir; Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="e2e52-114">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="e2e52-115">Dil</span><span class="sxs-lookup"><span data-stu-id="e2e52-115">Language</span></span>  
 <span data-ttu-id="e2e52-116">Dosya (. svc) içindeki tüm satır içi kodları derlerken kullanılan dili belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2e52-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="e2e52-117">Değerler herhangi birini temsil edebilir. Sırasıyla, Visual Basic .NET ve JScript C#.net 'e C#başvuran, vb ve JS dahil net destekli dil.</span><span class="sxs-lookup"><span data-stu-id="e2e52-117">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="e2e52-118">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e2e52-118">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="e2e52-119">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="e2e52-119">CodeBehind</span></span>  
 <span data-ttu-id="e2e52-120">XML Web hizmetini uygulayan sınıf aynı dosyada yer almıyor ve bir derlemeye derlenmediği ve \Bin dizinine yerleştirilebilecek olan XML Web hizmetini uygulayan kaynak dosyayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2e52-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2e52-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2e52-121">Remarks</span></span>  
 <span data-ttu-id="e2e52-122">Hizmeti <xref:System.ServiceModel.ServiceHost> barındırmak için kullanılan, Windows Communication Foundation (WCF) programlama modeli içindeki bir genişletilebilirlik noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="e2e52-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="e2e52-123">Bir fabrika deseninin, büyük olasılıkla barındırma ortamının <xref:System.ServiceModel.ServiceHost> doğrudan örneği bulunmayan çok biçimli bir tür olduğu için örneğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2e52-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="e2e52-124">Varsayılan uygulama, <xref:System.ServiceModel.ServiceHost>örneği <xref:System.ServiceModel.Activation.ServiceHostFactory> oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2e52-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="e2e52-125">Ancak, [ \@ServiceHost](servicehost.md) yönergesinde fabrika uygulamanızın clr türü adını belirterek kendi fabrikanızı (türetilmiş ana bilgisayarınızı döndüren bir tane) sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2e52-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [\@ServiceHost](servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="e2e52-126">Varsayılan fabrika yerine kendi özel hizmet ana bilgisayar fabrikasını kullanmak için, [@ServiceHost](servicehost.md) yönergede tür adını aşağıdaki gibi belirtmeniz yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="e2e52-126">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="e2e52-127">Fabrika uygulamalarını mümkün olduğunca ışık olarak tutun.</span><span class="sxs-lookup"><span data-stu-id="e2e52-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="e2e52-128">Çok sayıda özel mantığa sahipseniz, bu mantığı fabrika yerine ana bilgisayarınıza yerleştirirseniz, kodunuz daha yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2e52-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="e2e52-129">`MyService`Örneğin, için AJAX özellikli bir uç noktasını etkinleştirmek üzere, aşağıdaki örnekte gösterildiği <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> gibi, varsayılan <xref:System.ServiceModel.Activation.ServiceHostFactory> [@ServiceHost](servicehost.md) değer yerine `Factory` , öznitelik için değerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="e2e52-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2e52-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2e52-130">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2e52-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2e52-131">See also</span></span>

- [<span data-ttu-id="e2e52-132">Özel Hizmet Konağı</span><span class="sxs-lookup"><span data-stu-id="e2e52-132">Custom Service Host</span></span>](../../../wcf/samples/custom-service-host.md)
