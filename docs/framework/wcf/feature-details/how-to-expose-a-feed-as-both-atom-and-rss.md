---
title: 'Nasıl yapılır: Bir akışı hem Atom olarak kullanıma sunmak ve RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 43ad8ae0b12b07e2d0abe3e208f6d1ccdb2ec77d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681176"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="942fc-102">Nasıl yapılır: Bir akışı hem Atom olarak kullanıma sunmak ve RSS</span><span class="sxs-lookup"><span data-stu-id="942fc-102">How to: Expose a Feed as Both Atom and RSS</span></span>
<span data-ttu-id="942fc-103">Windows Communication Foundation (WCF), bir dağıtım akışı hizmetidir oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="942fc-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="942fc-104">Bu konu, bir dağıtım akışı hem Atom 1.0 hem de RSS 2.0 kullanarak kullanıma sunan bir dağıtım hizmetinin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="942fc-104">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="942fc-105">Bu hizmet ya da dağıtım biçimi döndüren bir uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="942fc-105">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="942fc-106">Kolaylık olması için bu örnekte kullanılan kendi kendine barındırılan hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="942fc-106">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="942fc-107">Bir üretim ortamında bu türde bir hizmet IIS ya da WAS altında barındırılması.</span><span class="sxs-lookup"><span data-stu-id="942fc-107">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="942fc-108">Barındırma seçenekleri farklı WCF hakkında daha fazla bilgi için bkz. [barındırma](../../../../docs/framework/wcf/feature-details/hosting.md).</span><span class="sxs-lookup"><span data-stu-id="942fc-108">For more information about the different WCF hosting options, see [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="942fc-109">Temel Sendikasyon hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="942fc-109">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="942fc-110">İle işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="942fc-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="942fc-111">Döndürür bir dağıtım akışı olarak sunulan her işlem bir <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> nesne.</span><span class="sxs-lookup"><span data-stu-id="942fc-111">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="942fc-112">Parametreler için Not <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="942fc-112">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="942fc-113">`UriTemplate` Bu hizmet işlemini çağırmak için kullanılan URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="942fc-113">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="942fc-114">Bu parametre için dize değişmez değerleri ve küme ayraçları içinde bir değişken içeriyor ({*biçimi*}).</span><span class="sxs-lookup"><span data-stu-id="942fc-114">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="942fc-115">Hizmet işlem için bu değişkeni karşılık gelen `format` parametresi.</span><span class="sxs-lookup"><span data-stu-id="942fc-115">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="942fc-116">Daha fazla bilgi için bkz. <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="942fc-116">For more information, see <xref:System.UriTemplate>.</span></span> <span data-ttu-id="942fc-117">`BodyStyle` Bu hizmet işlemi gönderip aldığı iletileri nasıl yazılır etkiler.</span><span class="sxs-lookup"><span data-stu-id="942fc-117">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="942fc-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> Altyapı tarafından tanımlanan XML öğeleri tarafından gönderilen ve alınan bu hizmet işlemi verileri kaydırılan değil belirtir.</span><span class="sxs-lookup"><span data-stu-id="942fc-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="942fc-119">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span><span class="sxs-lookup"><span data-stu-id="942fc-119">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="942fc-120">Kullanım <xref:System.ServiceModel.ServiceKnownTypeAttribute> bu arabirim, hizmet işlemleri tarafından döndürülen türlerini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="942fc-120">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2.  <span data-ttu-id="942fc-121">Hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="942fc-121">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  <span data-ttu-id="942fc-122">Oluşturma bir <xref:System.ServiceModel.Syndication.SyndicationFeed> nesnesi ve bir yazar, kategori ve açıklama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="942fc-122">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  <span data-ttu-id="942fc-123">Birkaç oluşturma <xref:System.ServiceModel.Syndication.SyndicationItem> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="942fc-123">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  <span data-ttu-id="942fc-124">Ekleme <xref:System.ServiceModel.Syndication.SyndicationItem> akışı nesneleri.</span><span class="sxs-lookup"><span data-stu-id="942fc-124">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  <span data-ttu-id="942fc-125">İstenen biçimi döndürmek için biçim parametresi'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="942fc-125">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="942fc-126">Ana bilgisayar hizmeti</span><span class="sxs-lookup"><span data-stu-id="942fc-126">To host the service</span></span>  
  
1.  <span data-ttu-id="942fc-127">Oluşturma bir <xref:System.ServiceModel.Web.WebServiceHost> nesne.</span><span class="sxs-lookup"><span data-stu-id="942fc-127">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="942fc-128"><xref:System.ServiceModel.Web.WebServiceHost> Sınıfı otomatik olarak ekler bir uç nokta hizmetin temel adresinde bir kod veya yapılandırma belirtilmediği sürece.</span><span class="sxs-lookup"><span data-stu-id="942fc-128">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="942fc-129">Bu örnekte, varsayılan uç nokta açıklanması uç nokta belirtilir.</span><span class="sxs-lookup"><span data-stu-id="942fc-129">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  <span data-ttu-id="942fc-130">Hizmet ana bilgisayarı'nı açın, akışın hizmetten yük, akışı görüntülemek ve kullanıcıyı ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="942fc-130">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="942fc-131">Bir HTTP GET ile GetBlog çağırmak için</span><span class="sxs-lookup"><span data-stu-id="942fc-131">To call GetBlog with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="942fc-132">Internet Explorer'ı açın, aşağıdaki URL'yi yazın ve ENTER tuşuna basın: `http://localhost:8000/BlogService/GetBlog`.</span><span class="sxs-lookup"><span data-stu-id="942fc-132">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span>
  
     <span data-ttu-id="942fc-133">Hizmetin taban adresi URL içerir (`http://localhost:8000/BlogService`), hizmetin göreli adresini uç nokta ve çağırmak için hizmet işlemi.</span><span class="sxs-lookup"><span data-stu-id="942fc-133">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="942fc-134">GetBlog() koddan çağırmak için</span><span class="sxs-lookup"><span data-stu-id="942fc-134">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="942fc-135">Oluşturma bir <xref:System.Xml.XmlReader> taban adresini ve çağırdığınız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="942fc-135">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="942fc-136">Statik çağrı <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> tümleştirilmesidir yöntemi <xref:System.Xml.XmlReader> oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="942fc-136">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="942fc-137">Bu hizmet işlemini çağırır ve yeni bir doldurur <xref:System.ServiceModel.Syndication.SyndicationFeed> hizmet işleminden döndürülen biçimlendirici ile.</span><span class="sxs-lookup"><span data-stu-id="942fc-137">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="942fc-138">Erişim akış nesnesi.</span><span class="sxs-lookup"><span data-stu-id="942fc-138">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="942fc-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="942fc-139">Example</span></span>  
 <span data-ttu-id="942fc-140">Bu örnek için listeleme tam kod aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="942fc-140">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="942fc-141">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="942fc-141">Compiling the Code</span></span>  
 <span data-ttu-id="942fc-142">Yukarıdaki kod derlenirken System.ServiceModel.dll ve System.ServiceModel.Web.dll başvuru.</span><span class="sxs-lookup"><span data-stu-id="942fc-142">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="942fc-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="942fc-143">See also</span></span>
- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
