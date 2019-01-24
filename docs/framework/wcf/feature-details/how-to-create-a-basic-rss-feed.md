---
title: 'Nasıl yapılır: Temel bir RSS akışı oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
ms.openlocfilehash: 1de8d252be4740ad2a23ce1074d772364529eecf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695575"
---
# <a name="how-to-create-a-basic-rss-feed"></a><span data-ttu-id="93fcc-102">Nasıl yapılır: Temel bir RSS akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="93fcc-102">How to: Create a Basic RSS Feed</span></span>
<span data-ttu-id="93fcc-103">Windows Communication Foundation (WCF), bir dağıtım akışı hizmetidir oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="93fcc-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="93fcc-104">Bu konu, bir RSS dağıtım akışı sunan bir dağıtım hizmetinin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="93fcc-104">This topic discusses how to create a syndication service that exposes an RSS syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="93fcc-105">Temel Sendikasyon hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="93fcc-105">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="93fcc-106">İle işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="93fcc-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="93fcc-107">Bir dağıtım akış döndürmelidir olarak sunulan her işlem bir <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> nesne.</span><span class="sxs-lookup"><span data-stu-id="93fcc-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> object.</span></span>  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="93fcc-108">Geçerli olan tüm hizmet işlemleri <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği, HTTP GET isteklerini eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="93fcc-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> attribute are mapped to HTTP GET requests.</span></span> <span data-ttu-id="93fcc-109">İşlemi farklı bir HTTP yöntemine eşleyin <xref:System.ServiceModel.Web.WebInvokeAttribute> yerine.</span><span class="sxs-lookup"><span data-stu-id="93fcc-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="93fcc-110">Daha fazla bilgi için [nasıl yapılır: Temel bir WCF Web HTTP hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span><span class="sxs-lookup"><span data-stu-id="93fcc-110">For more information, see [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2.  <span data-ttu-id="93fcc-111">Hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="93fcc-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3.  <span data-ttu-id="93fcc-112">Oluşturma bir <xref:System.ServiceModel.Syndication.SyndicationFeed> nesnesi ve bir yazar, kategori ve açıklama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="93fcc-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4.  <span data-ttu-id="93fcc-113">Birkaç oluşturma <xref:System.ServiceModel.Syndication.SyndicationItem> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="93fcc-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5.  <span data-ttu-id="93fcc-114">Ekleme <xref:System.ServiceModel.Syndication.SyndicationItem> akış.</span><span class="sxs-lookup"><span data-stu-id="93fcc-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> to the feed.</span></span>  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6.  <span data-ttu-id="93fcc-115">Akış döndürür.</span><span class="sxs-lookup"><span data-stu-id="93fcc-115">Return the feed.</span></span>  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a><span data-ttu-id="93fcc-116">Konağa bir hizmet</span><span class="sxs-lookup"><span data-stu-id="93fcc-116">To host a service</span></span>  
  
1.  <span data-ttu-id="93fcc-117">Oluşturma bir <xref:System.ServiceModel.Web.WebServiceHost> nesne.</span><span class="sxs-lookup"><span data-stu-id="93fcc-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2.  <span data-ttu-id="93fcc-118">Hizmet ana bilgisayarı'nı açın ve kullanıcı ENTER tuşuna bastığında kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="93fcc-118">Open the service host and wait until the user presses ENTER.</span></span>  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="93fcc-119">Bir HTTP GET ile GetBlog() çağırmak için</span><span class="sxs-lookup"><span data-stu-id="93fcc-119">To call GetBlog() with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="93fcc-120">Internet Explorer'ı açın, aşağıdaki URL'yi yazın ve ENTER tuşuna basın: `http://localhost:8000/BlogService/GetBlog`.</span><span class="sxs-lookup"><span data-stu-id="93fcc-120">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span> <span data-ttu-id="93fcc-121">Hizmetin taban adresi URL içerir (`http://localhost:8000/BlogService`), hizmetin göreli adresini uç nokta ve çağırmak için hizmet işlemi.</span><span class="sxs-lookup"><span data-stu-id="93fcc-121">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="93fcc-122">GetBlog() koddan çağırmak için</span><span class="sxs-lookup"><span data-stu-id="93fcc-122">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="93fcc-123">Oluşturma bir <xref:System.Xml.XmlReader> taban adresini ve çağırdığınız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="93fcc-123">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="93fcc-124">Statik çağrı <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> tümleştirilmesidir yöntemi <xref:System.Xml.XmlReader> oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="93fcc-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="93fcc-125">Bu hizmet işlemini çağırır ve yeni bir doldurur <xref:System.ServiceModel.Syndication.SyndicationFeed> hizmet işleminden döndürülen biçimlendirici ile.</span><span class="sxs-lookup"><span data-stu-id="93fcc-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="93fcc-126">Erişim akış nesnesi.</span><span class="sxs-lookup"><span data-stu-id="93fcc-126">Access the feed object.</span></span>  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="93fcc-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="93fcc-127">Example</span></span>  
 <span data-ttu-id="93fcc-128">Bu örnek için listeleme tam kod aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="93fcc-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="93fcc-129">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="93fcc-129">Compiling the Code</span></span>  
 <span data-ttu-id="93fcc-130">Yukarıdaki kod derlenirken System.ServiceModel.dll ve System.ServiceModel.Web.dll başvuru.</span><span class="sxs-lookup"><span data-stu-id="93fcc-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93fcc-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93fcc-131">See also</span></span>
- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
