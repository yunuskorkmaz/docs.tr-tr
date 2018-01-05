---
title: "Nasıl yapılır: Web Hizmetine Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b035f5922722a05759ff1e13514cc760a57d668
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="9fd06-102">Nasıl yapılır: Web Hizmetine Bağlama</span><span class="sxs-lookup"><span data-stu-id="9fd06-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="9fd06-103">Bu örnek nasıl Web hizmeti yöntem çağrıları tarafından döndürülen nesne bağlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9fd06-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fd06-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fd06-104">Example</span></span>  
 <span data-ttu-id="9fd06-105">Bu örnekte [MSDN ve TechNet yayımlama sistemi(MTPS) içerik hizmeti](http://go.microsoft.com/fwlink/?LinkId=95677) belirtilen belge tarafından desteklenen dillerin listesi alınamadı.</span><span class="sxs-lookup"><span data-stu-id="9fd06-105">This example uses the [MSDN/TechNet Publishing System (MTPS) Content Service](http://go.microsoft.com/fwlink/?LinkId=95677) to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="9fd06-106">Bir Web hizmetini çağırmadan önce bir başvuru oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9fd06-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="9fd06-107">Kullanarak MTPS hizmetine Web başvurusu oluşturmak için [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="9fd06-107">To create a Web reference to the MTPS service using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], follow the following steps:</span></span>  
  
1.  <span data-ttu-id="9fd06-108">Projenizde açmak [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fd06-108">Open your project in [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="9fd06-109">Gelen **proje** menüsünde tıklatın **Web Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="9fd06-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3.  <span data-ttu-id="9fd06-110">İletişim kutusunda ayarlanan **URL** için [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span><span class="sxs-lookup"><span data-stu-id="9fd06-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4.  <span data-ttu-id="9fd06-111">Tuşuna **Git** ve ardından **başvuru ekleme**.</span><span class="sxs-lookup"><span data-stu-id="9fd06-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="9fd06-112">Ardından, Web hizmeti yöntemi çağırın ve <xref:System.Windows.FrameworkElement.DataContext%2A> uygun denetim veya döndürülen nesne penceresine.</span><span class="sxs-lookup"><span data-stu-id="9fd06-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="9fd06-113">**GetContent** yöntemi MTPS hizmetinin başvuru alır **getContentRequest** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9fd06-113">The **GetContent** method of the MTPS service takes a reference to the **getContentRequest** object.</span></span> <span data-ttu-id="9fd06-114">Bu nedenle, aşağıdaki örnekte, ilk olarak istek nesnesini ayarlar:</span><span class="sxs-lookup"><span data-stu-id="9fd06-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="9fd06-115">Sonra <xref:System.Windows.FrameworkElement.DataContext%2A> , oluşturabilir nesnenin özelliklerini bağlamalar, ayarlanmadı <xref:System.Windows.FrameworkElement.DataContext%2A> ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="9fd06-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="9fd06-116">Bu örnekte, <xref:System.Windows.FrameworkElement.DataContext%2A> ayarlanır **getContentResponse** tarafından döndürülen nesne **GetContent** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9fd06-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the **getContentResponse** object returned by the **GetContent** method.</span></span> <span data-ttu-id="9fd06-117">Aşağıdaki örnekte, <xref:System.Windows.Controls.ItemsControl> bağlar ve görüntüler **yerel ayar** değerlerini **availableVersionsAndLocales** , **getContentResponse**.</span><span class="sxs-lookup"><span data-stu-id="9fd06-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the **locale** values of **availableVersionsAndLocales** of **getContentResponse**.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="9fd06-118">Yapısı hakkında bilgi için **getContentResponse**, bkz: [içerik hizmeti belgeleri](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span><span class="sxs-lookup"><span data-stu-id="9fd06-118">For information about the structure of **getContentResponse**, see [Content Service documentation](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd06-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fd06-119">See Also</span></span>  
 [<span data-ttu-id="9fd06-120">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9fd06-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="9fd06-121">Bağlama Kaynaklarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9fd06-121">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="9fd06-122">XAML'de Bağlama için Veriyi Kullanılabilir Yapma</span><span class="sxs-lookup"><span data-stu-id="9fd06-122">Make Data Available for Binding in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
