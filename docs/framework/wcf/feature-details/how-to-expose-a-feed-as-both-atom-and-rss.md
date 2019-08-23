---
title: 'Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: f31f24cfc18f2c56539fe2b4623d54fe77a27797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950604"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="be487-102">Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma</span><span class="sxs-lookup"><span data-stu-id="be487-102">How to: Expose a Feed as Both Atom and RSS</span></span>
<span data-ttu-id="be487-103">Windows Communication Foundation (WCF), bir dağıtım akışı sunan bir hizmet oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="be487-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="be487-104">Bu konu, hem Atom 1,0 hem de RSS 2,0 kullanarak bir dağıtım akışı sunan bir dağıtım hizmeti oluşturmayı açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="be487-104">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="be487-105">Bu hizmet, bir dağıtım biçimi döndüren bir uç noktayı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="be487-105">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="be487-106">Basitlik için, bu örnekte kullanılan hizmetin kendine barındırıldığı yer vardır.</span><span class="sxs-lookup"><span data-stu-id="be487-106">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="be487-107">Üretim ortamında, bu türde bir hizmet IIS veya WAS altında barındırılır.</span><span class="sxs-lookup"><span data-stu-id="be487-107">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="be487-108">Farklı WCF barındırma seçenekleri hakkında daha fazla bilgi için bkz. [barındırma](../../../../docs/framework/wcf/feature-details/hosting.md).</span><span class="sxs-lookup"><span data-stu-id="be487-108">For more information about the different WCF hosting options, see [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="be487-109">Temel bir dağıtım hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="be487-109">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="be487-110"><xref:System.ServiceModel.Web.WebGetAttribute> Özniteliği ile işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="be487-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="be487-111">Bir dağıtım akışı olarak sunulan her işlem, bir <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="be487-111">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="be487-112">İçin parametreleri aklınızda edin <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="be487-112">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="be487-113">`UriTemplate`Bu hizmet işlemini çağırmak için kullanılan URL 'YI belirtir.</span><span class="sxs-lookup"><span data-stu-id="be487-113">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="be487-114">Bu parametre için dize, sabit değer ve küme ayracı ({*Format*}) içinde bir değişken içerir.</span><span class="sxs-lookup"><span data-stu-id="be487-114">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="be487-115">Bu değişken, hizmet işleminin `format` parametresine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="be487-115">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="be487-116">Daha fazla bilgi için bkz. <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="be487-116">For more information, see <xref:System.UriTemplate>.</span></span> <span data-ttu-id="be487-117">`BodyStyle`Bu hizmet işleminin gönderdiği ve aldığı iletilerin nasıl yazıldığını etkiler.</span><span class="sxs-lookup"><span data-stu-id="be487-117">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="be487-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare>Bu hizmet işlemine gönderilen ve bu hizmetten gönderilen verilerin altyapı tanımlı XML öğeleri tarafından kaydırılmayacağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="be487-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="be487-119">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span><span class="sxs-lookup"><span data-stu-id="be487-119">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="be487-120">Bu arabirimdeki hizmet işlemleri tarafından döndürülen türleri belirtmek içinöğesinikullanın.<xref:System.ServiceModel.ServiceKnownTypeAttribute></span><span class="sxs-lookup"><span data-stu-id="be487-120">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2. <span data-ttu-id="be487-121">Hizmet sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="be487-121">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. <span data-ttu-id="be487-122">Bir <xref:System.ServiceModel.Syndication.SyndicationFeed> nesne oluşturun ve yazar, kategori ve açıklama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="be487-122">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. <span data-ttu-id="be487-123">Birkaç <xref:System.ServiceModel.Syndication.SyndicationItem> nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="be487-123">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. <span data-ttu-id="be487-124"><xref:System.ServiceModel.Syndication.SyndicationItem> Nesneleri akışa ekleyin.</span><span class="sxs-lookup"><span data-stu-id="be487-124">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. <span data-ttu-id="be487-125">İstenen biçimi döndürmek için biçim parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="be487-125">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="be487-126">Hizmeti barındırmak için</span><span class="sxs-lookup"><span data-stu-id="be487-126">To host the service</span></span>  
  
1. <span data-ttu-id="be487-127">Bir <xref:System.ServiceModel.Web.WebServiceHost> nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="be487-127">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="be487-128">Kod <xref:System.ServiceModel.Web.WebServiceHost> veya yapılandırmada belirtilmemişse, sınıf otomatik olarak hizmetin temel adresinde bir uç nokta ekler.</span><span class="sxs-lookup"><span data-stu-id="be487-128">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="be487-129">Bu örnekte, varsayılan uç noktanın açığa çıkarılması için uç nokta belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="be487-129">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. <span data-ttu-id="be487-130">Hizmet konağını açın, hizmetten akışı yükleyin, akışı görüntüleyin ve kullanıcının ENTER tuşuna basması için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="be487-130">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="be487-131">Getblogi HTTP GET ile çağırmak için</span><span class="sxs-lookup"><span data-stu-id="be487-131">To call GetBlog with an HTTP GET</span></span>  
  
1. <span data-ttu-id="be487-132">Internet Explorer 'ı açın, aşağıdaki URL 'yi yazın ve ENTER tuşuna basın `http://localhost:8000/BlogService/GetBlog`:.</span><span class="sxs-lookup"><span data-stu-id="be487-132">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span>
  
     <span data-ttu-id="be487-133">URL, hizmetin temel adresini (`http://localhost:8000/BlogService`), bitiş noktasının göreli adresini ve çağrılacak hizmet işlemini içerir.</span><span class="sxs-lookup"><span data-stu-id="be487-133">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="be487-134">Koddan GetBlog () çağırmak için</span><span class="sxs-lookup"><span data-stu-id="be487-134">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="be487-135">Temel adresi <xref:System.Xml.XmlReader> ve aradığınız yöntemi içeren bir oluşturun.</span><span class="sxs-lookup"><span data-stu-id="be487-135">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="be487-136">Yeni oluşturduğunuz ' <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> ı geçirerek <xref:System.Xml.XmlReader> statik yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="be487-136">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="be487-137">Bu, hizmet işlemini çağırır ve hizmet işleminden döndürülen <xref:System.ServiceModel.Syndication.SyndicationFeed> biçimlendirici ile yeni bir doldurur.</span><span class="sxs-lookup"><span data-stu-id="be487-137">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="be487-138">Akış nesnesine erişin.</span><span class="sxs-lookup"><span data-stu-id="be487-138">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="be487-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="be487-139">Example</span></span>  
 <span data-ttu-id="be487-140">Bu örnek için tam kod listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="be487-140">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="be487-141">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="be487-141">Compiling the Code</span></span>  
 <span data-ttu-id="be487-142">Yukarıdaki kod derlenirken, System. ServiceModel. dll ve System. ServiceModel. Web. dll ' ye başvurun.</span><span class="sxs-lookup"><span data-stu-id="be487-142">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be487-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be487-143">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
