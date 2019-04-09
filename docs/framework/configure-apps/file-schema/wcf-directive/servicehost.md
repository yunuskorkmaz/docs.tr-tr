---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 3102ae8d8c28be43883eeaff6c4f829b355384a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111403"
---
# <a name="servicehost"></a><span data-ttu-id="508f8-101">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="508f8-101">\@ServiceHost</span></span>
<span data-ttu-id="508f8-102">Barındırılan hizmet konak hizmeti ile üretmek için kullanılan Üreteç ve erişmek veya .svc dosyasında sağlanan barındırma Kodu derlemek için gereken diğer programlama özelliklerini ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="508f8-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="508f8-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="508f8-103">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="508f8-104">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="508f8-104">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="508f8-105">Hizmet</span><span class="sxs-lookup"><span data-stu-id="508f8-105">Service</span></span>  
 <span data-ttu-id="508f8-106">Barındırılan hizmet CLR türü adı.</span><span class="sxs-lookup"><span data-stu-id="508f8-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="508f8-107">Bu, bir veya daha fazla hizmet kişileri uygulayan bir tür tam bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="508f8-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="508f8-108">Fabrika</span><span class="sxs-lookup"><span data-stu-id="508f8-108">Factory</span></span>  
 <span data-ttu-id="508f8-109">Hizmet ana bilgisayarı örneği oluşturmak için kullanılan hizmet barındırma ortamı fabrikası CLR türü adı.</span><span class="sxs-lookup"><span data-stu-id="508f8-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="508f8-110">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="508f8-110">This attribute is optional.</span></span> <span data-ttu-id="508f8-111">Belirtilmemişse, varsayılan <xref:System.ServiceModel.Activation.ServiceHostFactory> kullanılan örneğini döndüren <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="508f8-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="508f8-112">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="508f8-112">Debug</span></span>  
 <span data-ttu-id="508f8-113">Windows Communication Foundation (WCF) hizmet hata ayıklama sembolleriyle derlenmiş olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="508f8-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> `true` <span data-ttu-id="508f8-114">WCF hizmet hata ayıklama sembolleriyle derlenmiş Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="508f8-114">if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="508f8-115">Dil</span><span class="sxs-lookup"><span data-stu-id="508f8-115">Language</span></span>  
 <span data-ttu-id="508f8-116">Dosya (.svc) içindeki tüm satır içi kod derlenirken kullanılan dili belirtir.</span><span class="sxs-lookup"><span data-stu-id="508f8-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="508f8-117">Değerlerin herhangi temsil edebilir. C#, VB ve C#, Visual Basic .NET ve JScript .NET için sırasıyla başvuran JS dahil olmak üzere ağ tarafından desteklenen dil.</span><span class="sxs-lookup"><span data-stu-id="508f8-117">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="508f8-118">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="508f8-118">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="508f8-119">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="508f8-119">CodeBehind</span></span>  
 <span data-ttu-id="508f8-120">XML Web hizmeti XML Web hizmeti uygulayan sınıfı aynı dosyada bulunmadığı ve edilmemiş bir bütünleştirilmiş kod içine derlenmiş ve \Bin dizinine olduğunda uygulayan kaynak dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="508f8-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="508f8-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="508f8-121">Remarks</span></span>  
 <span data-ttu-id="508f8-122"><xref:System.ServiceModel.ServiceHost> Hizmeti barındırmak için kullanılan bir Windows Communication Foundation (WCF) programlama modeli içinde genişletilebilirlik noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="508f8-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="508f8-123">Fabrika düzeni örneği oluşturmak için kullanılan <xref:System.ServiceModel.ServiceHost> , büyük olasılıkla barındırma ortamı doğrudan örneğini oluşturmalıdır değil polimorfik bir tür olduğundan.</span><span class="sxs-lookup"><span data-stu-id="508f8-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="508f8-124">Varsayılan uygulama kullanan <xref:System.ServiceModel.Activation.ServiceHostFactory> bir örneğini oluşturmak için <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="508f8-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="508f8-125">Ancak, Fabrika uygulamanızda CLR tür adını belirterek kendi Fabrika (bir türetilmiş ana döndürür) sağlayabilirsiniz [ \@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi.</span><span class="sxs-lookup"><span data-stu-id="508f8-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [\@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="508f8-126">Kendi özel hizmet barındırma ortamı fabrikası yerine varsayılan fabrika kullanmak için yalnızca tür adı sağlayın [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="508f8-126">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="508f8-127">Fabrika uygulamaları olabildiğince hafif tutun.</span><span class="sxs-lookup"><span data-stu-id="508f8-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="508f8-128">Özel mantığı çok sayıda varsa, kod içinde yerine ana Fabrika içinde bu mantığı koyarsanız daha yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="508f8-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="508f8-129">Örneğin, için AJAX etkinleştirilmiş uç noktayı etkinleştirme `MyService`, belirtin <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> değerini `Factory` varsayılan yerine bir öznitelik <xref:System.ServiceModel.Activation.ServiceHostFactory>, [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönerge olarak Aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="508f8-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="508f8-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="508f8-130">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="508f8-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="508f8-131">See also</span></span>

- [<span data-ttu-id="508f8-132">Özel Hizmet Ana Bilgisayarı</span><span class="sxs-lookup"><span data-stu-id="508f8-132">Custom Service Host</span></span>](../../../../../docs/framework/wcf/samples/custom-service-host.md)
