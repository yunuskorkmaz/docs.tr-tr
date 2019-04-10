---
title: 'Nasıl yapılır: Web Hizmetine Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
ms.openlocfilehash: 2c3bc1f2142f07aba3df2da6c46117d3907443a5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304993"
---
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="9134a-102">Nasıl yapılır: Web Hizmetine Bağlama</span><span class="sxs-lookup"><span data-stu-id="9134a-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="9134a-103">Bu örnekte, Web hizmeti yöntem çağrıları tarafından döndürülen nesnelere bağlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9134a-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9134a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9134a-104">Example</span></span>  
 <span data-ttu-id="9134a-105">Bu örnekte [MSDN/TechNet yayımlama sistemi(MTPS) içerik hizmeti](https://go.microsoft.com/fwlink/?LinkId=95677) belirtilen bir belge tarafından desteklenen dillerin listesini almak için.</span><span class="sxs-lookup"><span data-stu-id="9134a-105">This example uses the [MSDN/TechNet Publishing System (MTPS) Content Service](https://go.microsoft.com/fwlink/?LinkId=95677) to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="9134a-106">Bir Web hizmeti çağırmadan önce buna bir başvuru oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9134a-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="9134a-107">MTPS hizmeti kullanarak bir Web başvurusu [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="9134a-107">To create a Web reference to the MTPS service using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], follow the following steps:</span></span>  
  
1. <span data-ttu-id="9134a-108">İçerisinde projenizi açın [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9134a-108">Open your project in [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span></span>  
  
2. <span data-ttu-id="9134a-109">Gelen **proje** menüsünde tıklatın **Web başvurusu Ekle'yi**.</span><span class="sxs-lookup"><span data-stu-id="9134a-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3. <span data-ttu-id="9134a-110">İletişim kutusunda ayarlanan **URL** için [ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl ](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span><span class="sxs-lookup"><span data-stu-id="9134a-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4. <span data-ttu-id="9134a-111">Tuşuna **Git** ardından **Başvurusu Ekle**.</span><span class="sxs-lookup"><span data-stu-id="9134a-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="9134a-112">Ardından, Web hizmeti yöntemi çağırmanızı ve <xref:System.Windows.FrameworkElement.DataContext%2A> uygun denetim ya da penceresine döndürülen nesne.</span><span class="sxs-lookup"><span data-stu-id="9134a-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="9134a-113">**GetContent** MTPS hizmetinin yöntemi, bir başvuru alır **getContentRequest** nesne.</span><span class="sxs-lookup"><span data-stu-id="9134a-113">The **GetContent** method of the MTPS service takes a reference to the **getContentRequest** object.</span></span> <span data-ttu-id="9134a-114">Bu nedenle, aşağıdaki örnekte, ilk olarak istek nesnesini ayarlar:</span><span class="sxs-lookup"><span data-stu-id="9134a-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="9134a-115">Sonra <xref:System.Windows.FrameworkElement.DataContext%2A> , oluşturabilir nesnenin özelliklerini bağlar, ayarlanmadı <xref:System.Windows.FrameworkElement.DataContext%2A> ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="9134a-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="9134a-116">Bu örnekte, <xref:System.Windows.FrameworkElement.DataContext%2A> ayarlanır **getContentResponse** tarafından döndürülen nesne **GetContent** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9134a-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the **getContentResponse** object returned by the **GetContent** method.</span></span> <span data-ttu-id="9134a-117">Aşağıdaki örnekte, <xref:System.Windows.Controls.ItemsControl> bağlar ve görüntüler **yerel** değerlerini **availableVersionsAndLocales** , **getContentResponse**.</span><span class="sxs-lookup"><span data-stu-id="9134a-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the **locale** values of **availableVersionsAndLocales** of **getContentResponse**.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="9134a-118">Yapısı hakkında bilgi için **getContentResponse**, bkz: [içerik hizmeti belgeleri](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span><span class="sxs-lookup"><span data-stu-id="9134a-118">For information about the structure of **getContentResponse**, see [Content Service documentation](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9134a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9134a-119">See also</span></span>

- [<span data-ttu-id="9134a-120">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9134a-120">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="9134a-121">Kaynakların Bağlanmasına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9134a-121">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="9134a-122">XAML'de Bağlama için Veriyi Kullanılabilir Yapma</span><span class="sxs-lookup"><span data-stu-id="9134a-122">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
