---
title: 'Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: e4ce1fa7b494c2317a1bddc57ee6b150c84b9a96
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593152"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="68e33-102">Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma</span><span class="sxs-lookup"><span data-stu-id="68e33-102">How to: Expose a Feed as Both Atom and RSS</span></span>
<span data-ttu-id="68e33-103">Windows Communication Foundation (WCF), bir dağıtım akışı sunan bir hizmet oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="68e33-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="68e33-104">Bu konu, hem Atom 1,0 hem de RSS 2,0 kullanarak bir dağıtım akışı sunan bir dağıtım hizmeti oluşturmayı açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="68e33-104">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="68e33-105">Bu hizmet, bir dağıtım biçimi döndüren bir uç noktayı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="68e33-105">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="68e33-106">Basitlik için, bu örnekte kullanılan hizmetin kendine barındırıldığı yer vardır.</span><span class="sxs-lookup"><span data-stu-id="68e33-106">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="68e33-107">Üretim ortamında, bu türde bir hizmet IIS veya WAS altında barındırılır.</span><span class="sxs-lookup"><span data-stu-id="68e33-107">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="68e33-108">Farklı WCF barındırma seçenekleri hakkında daha fazla bilgi için bkz. [barındırma](hosting.md).</span><span class="sxs-lookup"><span data-stu-id="68e33-108">For more information about the different WCF hosting options, see [Hosting](hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="68e33-109">Temel bir dağıtım hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="68e33-109">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="68e33-110">Özniteliği ile işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesi tanımlayın <xref:System.ServiceModel.Web.WebGetAttribute> .</span><span class="sxs-lookup"><span data-stu-id="68e33-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="68e33-111">Bir dağıtım akışı olarak sunulan her işlem, bir nesnesi döndürür <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> .</span><span class="sxs-lookup"><span data-stu-id="68e33-111">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="68e33-112">İçin parametreleri aklınızda edin <xref:System.ServiceModel.Web.WebGetAttribute> .</span><span class="sxs-lookup"><span data-stu-id="68e33-112">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="68e33-113">`UriTemplate`Bu hizmet işlemini çağırmak için kullanılan URL 'YI belirtir.</span><span class="sxs-lookup"><span data-stu-id="68e33-113">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="68e33-114">Bu parametre için dize, sabit değer ve küme ayracı ({*Format*}) içinde bir değişken içerir.</span><span class="sxs-lookup"><span data-stu-id="68e33-114">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="68e33-115">Bu değişken, hizmet işleminin parametresine karşılık gelir `format` .</span><span class="sxs-lookup"><span data-stu-id="68e33-115">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="68e33-116">Daha fazla bilgi için bkz. <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="68e33-116">For more information, see <xref:System.UriTemplate>.</span></span> <span data-ttu-id="68e33-117">`BodyStyle`Bu hizmet işleminin gönderdiği ve aldığı iletilerin nasıl yazıldığını etkiler.</span><span class="sxs-lookup"><span data-stu-id="68e33-117">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="68e33-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare>Bu hizmet işlemine gönderilen ve bu hizmetten gönderilen verilerin altyapı tanımlı XML öğeleri tarafından kaydırılmayacağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="68e33-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="68e33-119">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span><span class="sxs-lookup"><span data-stu-id="68e33-119">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="68e33-120"><xref:System.ServiceModel.ServiceKnownTypeAttribute>Bu arabirimdeki hizmet işlemleri tarafından döndürülen türleri belirtmek için öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="68e33-120">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2. <span data-ttu-id="68e33-121">Hizmet sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="68e33-121">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. <span data-ttu-id="68e33-122">Bir <xref:System.ServiceModel.Syndication.SyndicationFeed> nesne oluşturun ve yazar, kategori ve açıklama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="68e33-122">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. <span data-ttu-id="68e33-123">Birkaç <xref:System.ServiceModel.Syndication.SyndicationItem> nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="68e33-123">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. <span data-ttu-id="68e33-124"><xref:System.ServiceModel.Syndication.SyndicationItem>Nesneleri akışa ekleyin.</span><span class="sxs-lookup"><span data-stu-id="68e33-124">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. <span data-ttu-id="68e33-125">İstenen biçimi döndürmek için biçim parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="68e33-125">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="68e33-126">Hizmeti barındırmak için</span><span class="sxs-lookup"><span data-stu-id="68e33-126">To host the service</span></span>  
  
1. <span data-ttu-id="68e33-127">Bir <xref:System.ServiceModel.Web.WebServiceHost> nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="68e33-127">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="68e33-128"><xref:System.ServiceModel.Web.WebServiceHost>Kod veya yapılandırmada belirtilmemişse, sınıf otomatik olarak hizmetin temel adresinde bir uç nokta ekler.</span><span class="sxs-lookup"><span data-stu-id="68e33-128">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="68e33-129">Bu örnekte, varsayılan uç noktanın açığa çıkarılması için uç nokta belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="68e33-129">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. <span data-ttu-id="68e33-130">Hizmet konağını açın, hizmetten akışı yükleyin, akışı görüntüleyin ve kullanıcının ENTER tuşuna basması için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="68e33-130">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="68e33-131">Getblogi HTTP GET ile çağırmak için</span><span class="sxs-lookup"><span data-stu-id="68e33-131">To call GetBlog with an HTTP GET</span></span>  
  
1. <span data-ttu-id="68e33-132">Internet Explorer 'ı açın, aşağıdaki URL 'yi yazın ve ENTER tuşuna basın: `http://localhost:8000/BlogService/GetBlog` .</span><span class="sxs-lookup"><span data-stu-id="68e33-132">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span>
  
     <span data-ttu-id="68e33-133">URL, hizmetin temel adresini ( `http://localhost:8000/BlogService` ), bitiş noktasının göreli adresini ve çağrılacak hizmet işlemini içerir.</span><span class="sxs-lookup"><span data-stu-id="68e33-133">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="68e33-134">Koddan GetBlog () çağırmak için</span><span class="sxs-lookup"><span data-stu-id="68e33-134">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="68e33-135"><xref:System.Xml.XmlReader>Temel adresi ve aradığınız yöntemi içeren bir oluşturun.</span><span class="sxs-lookup"><span data-stu-id="68e33-135">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="68e33-136"><xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29>Yeni oluşturduğunuz ' ı geçirerek statik yöntemi çağırın <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="68e33-136">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="68e33-137">Bu, hizmet işlemini çağırır ve <xref:System.ServiceModel.Syndication.SyndicationFeed> hizmet işleminden döndürülen biçimlendirici ile yeni bir doldurur.</span><span class="sxs-lookup"><span data-stu-id="68e33-137">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="68e33-138">Akış nesnesine erişin.</span><span class="sxs-lookup"><span data-stu-id="68e33-138">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="68e33-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="68e33-139">Example</span></span>  
 <span data-ttu-id="68e33-140">Bu örnek için tam kod listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="68e33-140">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="68e33-141">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="68e33-141">Compiling the Code</span></span>  
 <span data-ttu-id="68e33-142">Yukarıdaki kod derlenirken, System. ServiceModel. dll ve System. ServiceModel. Web. dll ' ye başvurun.</span><span class="sxs-lookup"><span data-stu-id="68e33-142">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e33-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68e33-143">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
