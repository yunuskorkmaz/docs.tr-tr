---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 5498c300ab126bbc4e08cd228e3e7b48e905932e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352550"
---
# <a name="servicehost"></a>@ServiceHost
<span data-ttu-id="0ada9-101">Barındırılacak şekilde hizmet ana bilgisayar hizmeti ile üretmek için kullanılan Üreteç ve erişim veya .svc dosyasında sağlanan barındırma Kodu derlemek için gereken diğer programlama özelliklerini ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="0ada9-101">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ada9-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ada9-102">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="0ada9-103">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0ada9-103">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="0ada9-104">Hizmet</span><span class="sxs-lookup"><span data-stu-id="0ada9-104">Service</span></span>  
 <span data-ttu-id="0ada9-105">Barındırılan hizmete CLR türü adı.</span><span class="sxs-lookup"><span data-stu-id="0ada9-105">The CLR type name of the service hosted.</span></span> <span data-ttu-id="0ada9-106">Bu, bir veya daha fazla hizmet kişileri uygulayan bir tür tam bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ada9-106">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="0ada9-107">Fabrika</span><span class="sxs-lookup"><span data-stu-id="0ada9-107">Factory</span></span>  
 <span data-ttu-id="0ada9-108">Hizmet ana bilgisayarı örneği oluşturmak için kullanılan hizmet ana bilgisayar üreteci CLR türü adı.</span><span class="sxs-lookup"><span data-stu-id="0ada9-108">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="0ada9-109">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ada9-109">This attribute is optional.</span></span> <span data-ttu-id="0ada9-110">Belirtilmezse, varsayılan <xref:System.ServiceModel.Activation.ServiceHostFactory> kullanılan örneğini döndüren <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="0ada9-110">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="0ada9-111">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="0ada9-111">Debug</span></span>  
 <span data-ttu-id="0ada9-112">Windows Communication Foundation (WCF) hizmetini hata ayıklama sembolleriyle derlenip derlenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ada9-112">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="0ada9-113">`true` WCF Hizmeti hata ayıklama sembolleriyle derlenip Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="0ada9-113">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="0ada9-114">Dil</span><span class="sxs-lookup"><span data-stu-id="0ada9-114">Language</span></span>  
 <span data-ttu-id="0ada9-115">Dosya (.svc) içindeki tüm satır içi kod derleme sırasında kullanılan dili belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ada9-115">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="0ada9-116">Değerler herhangi temsil edebilir. C#, VB ve C#, Visual Basic .NET ve JScript .NET sırasıyla başvuru JS içeren NET desteklenen dili.</span><span class="sxs-lookup"><span data-stu-id="0ada9-116">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="0ada9-117">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ada9-117">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="0ada9-118">Arkasındaki koda</span><span class="sxs-lookup"><span data-stu-id="0ada9-118">CodeBehind</span></span>  
 <span data-ttu-id="0ada9-119">XML Web hizmeti uygulayan sınıf aynı dosyada bulunmuyor ve edilmemiş bütünleştirilmiş koda derlenmemiş ve \Bin dizinine yerleştirilen yükleyen XML Web hizmeti uygulayan kaynak dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ada9-119">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ada9-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ada9-120">Remarks</span></span>  
 <span data-ttu-id="0ada9-121"><xref:System.ServiceModel.ServiceHost> Hizmet barındırmak için kullanılan Windows Communication Foundation (WCF) programlama modeli içindeki genişletilebilirlik noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="0ada9-121">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="0ada9-122">Fabrika düzeni örneği oluşturmak için kullanılan <xref:System.ServiceModel.ServiceHost> , büyük olasılıkla barındırma ortamı doğrudan örneği değil çok biçimli bir tür olduğundan.</span><span class="sxs-lookup"><span data-stu-id="0ada9-122">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="0ada9-123">Varsayılan uygulama kullanan <xref:System.ServiceModel.Activation.ServiceHostFactory> bir örneğini oluşturmak için <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="0ada9-123">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="0ada9-124">Ancak Fabrika uygulamanızda CLR türü adını belirterek kendi Fabrika (bir türetilmiş ana bilgisayarınız döndürür) sağlayabilir [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi.</span><span class="sxs-lookup"><span data-stu-id="0ada9-124">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="0ada9-125">Varsayılan fabrika yerine kendi özel hizmet ana bilgisayar üreteci kullanmak için yalnızca ın türü adını belirtin [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) şekilde yönergesi:</span><span class="sxs-lookup"><span data-stu-id="0ada9-125">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="0ada9-126">Fabrika uygulamaları olabildiğince hafif tutun.</span><span class="sxs-lookup"><span data-stu-id="0ada9-126">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="0ada9-127">Çok sayıda özel mantık varsa, kodunuzu yerine, konak Fabrika içinde içinde bu mantığı yerleştirirseniz daha yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0ada9-127">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="0ada9-128">Örneğin, bir AJAX etkinleştirilmiş uç nokta için etkinleştirmek için `MyService`, belirtin <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> değerini `Factory` varsayılan yerine özniteliği <xref:System.ServiceModel.Activation.ServiceHostFactory>, [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) olarak yönergesi Aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="0ada9-128">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ada9-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ada9-129">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ada9-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ada9-130">See Also</span></span>  
 [<span data-ttu-id="0ada9-131">Özel Hizmet Konağı</span><span class="sxs-lookup"><span data-stu-id="0ada9-131">Custom Service Host</span></span>](../../../../../docs/framework/wcf/samples/custom-service-host.md)
