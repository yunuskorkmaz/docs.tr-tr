---
title: 'Nasıl Yapılır: Temel Bir Atom Akışı Oluşturma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 26e5bf0771e3b8d700efeaf4f63b9866534db68a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-create-a-basic-atom-feed"></a><span data-ttu-id="f180b-102">Nasıl Yapılır: Temel Bir Atom Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f180b-102">How to: Create a Basic Atom Feed</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="f180b-103"> Akış bir dağıtım kullanıma sunan bir hizmet oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f180b-103"> allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="f180b-104">Bu konu, akışı bir Atom dağıtım gösteren bir dağıtım hizmetin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f180b-104">This topic discusses how to create a syndication service that exposes an Atom syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="f180b-105">Bir temel dağıtım hizmet oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f180b-105">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="f180b-106">İle işaretlenen arabirimini kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f180b-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="f180b-107">Bir dağıtım akışı döndürmelidir olarak sunulan her işlem bir <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f180b-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> object.</span></span>  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="f180b-108">Geçerli tüm hizmet işlemleri <xref:System.ServiceModel.Web.WebGetAttribute> HTTP GET isteklerine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f180b-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> are mapped to HTTP GET requests.</span></span> <span data-ttu-id="f180b-109">İşlemi farklı bir HTTP yöntem eşleyin <xref:System.ServiceModel.Web.WebInvokeAttribute> yerine.</span><span class="sxs-lookup"><span data-stu-id="f180b-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="f180b-110">Daha fazla bilgi için bkz: [nasıl yapılır: temel bir WCF Web HTTP hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span><span class="sxs-lookup"><span data-stu-id="f180b-110">For more information, see [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2.  <span data-ttu-id="f180b-111">Hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="f180b-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3.  <span data-ttu-id="f180b-112">Oluşturma bir <xref:System.ServiceModel.Syndication.SyndicationFeed> nesne ve yazar, kategori ve açıklama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f180b-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4.  <span data-ttu-id="f180b-113">Birkaç oluşturmak <xref:System.ServiceModel.Syndication.SyndicationItem> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f180b-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5.  <span data-ttu-id="f180b-114">Ekleme <xref:System.ServiceModel.Syndication.SyndicationItem> akışa nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f180b-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6.  <span data-ttu-id="f180b-115">Akış döndür.</span><span class="sxs-lookup"><span data-stu-id="f180b-115">Return the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="f180b-116">Ana bilgisayar hizmeti</span><span class="sxs-lookup"><span data-stu-id="f180b-116">To host the service</span></span>  
  
1.  <span data-ttu-id="f180b-117">Oluşturma bir <xref:System.ServiceModel.Web.WebServiceHost> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f180b-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2.  <span data-ttu-id="f180b-118">Hizmet ana bilgisayarı açın, akışı hizmetten yüklenemiyor, akışı görüntülemek ve ENTER tuşuna basın kullanıcıya için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="f180b-118">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="f180b-119">Bir HTTP GET ile GetBlog() çağırmak için</span><span class="sxs-lookup"><span data-stu-id="f180b-119">To call GetBlog() with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="f180b-120">Internet Explorer'ı açın, aşağıdaki URL'yi yazın ve ENTER tuşuna basın: http://localhost:8000/BlogService/GetBlog</span><span class="sxs-lookup"><span data-stu-id="f180b-120">Open Internet Explorer, type the following URL, and press ENTER: http://localhost:8000/BlogService/GetBlog</span></span>  
  
     <span data-ttu-id="f180b-121">Hizmetin taban adresi URL içerir (http://localhost:8000/BlogService), göreli adresi uç nokta ve hizmet işlemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="f180b-121">The URL contains the base address of the service (http://localhost:8000/BlogService), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="f180b-122">Koddan GetBlog() çağırmak için</span><span class="sxs-lookup"><span data-stu-id="f180b-122">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="f180b-123">Oluşturma bir <xref:System.Xml.XmlReader> taban adresini ve çağırdığınız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f180b-123">Create a <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="f180b-124">Statik çağrısı <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> tümleştirilmesidir yöntemi <xref:System.Xml.XmlReader> , yeni oluşturduğunuz.</span><span class="sxs-lookup"><span data-stu-id="f180b-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="f180b-125">Bu hizmet işlemini çağırır ve yeni bir doldurur <xref:System.ServiceModel.Syndication.SyndicationFeed> hizmet işleminden döndürülen biçimlendirici ile.</span><span class="sxs-lookup"><span data-stu-id="f180b-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="f180b-126">Erişim akış nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f180b-126">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="f180b-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="f180b-127">Example</span></span>  
 <span data-ttu-id="f180b-128">Bu örnek için listeleme tam kod aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f180b-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f180b-129">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f180b-129">Compiling the Code</span></span>  
 <span data-ttu-id="f180b-130">Önceki kod derlerken System.ServiceModel.dll ve System.ServiceModel.Web.dll başvuru.</span><span class="sxs-lookup"><span data-stu-id="f180b-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f180b-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f180b-131">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
