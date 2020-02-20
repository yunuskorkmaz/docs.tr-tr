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
ms.openlocfilehash: 3a3f6edc974448ddab9fe30e97bdc1130d3b97dc
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449978"
---
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="ff515-102">Nasıl yapılır: Web Hizmetine Bağlama</span><span class="sxs-lookup"><span data-stu-id="ff515-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="ff515-103">Bu örnek, Web hizmeti yöntem çağrıları tarafından döndürülen nesnelere nasıl bağlanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff515-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff515-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff515-104">Example</span></span>  
 <span data-ttu-id="ff515-105">Bu örnek, belirtilen bir belge tarafından desteklenen dillerin listesini almak için MSDN/TechNet yayımlama sistemi (MTPS) Içerik hizmetini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff515-105">This example uses the MSDN/TechNet Publishing System (MTPS) Content Service to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="ff515-106">Bir Web hizmetini çağırmak için bir başvuru oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff515-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="ff515-107">Visual Studio kullanarak MTPS hizmetine bir Web başvurusu oluşturmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="ff515-107">To create a Web reference to the MTPS service using Visual Studio, follow the following steps:</span></span>  
  
1. <span data-ttu-id="ff515-108">Projenizi Visual Studio 'da açın.</span><span class="sxs-lookup"><span data-stu-id="ff515-108">Open your project in Visual Studio.</span></span>  
  
2. <span data-ttu-id="ff515-109">**Proje** menüsünden **Web başvurusu Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ff515-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3. <span data-ttu-id="ff515-110">İletişim kutusunda **URL 'yi** [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl)olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ff515-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4. <span data-ttu-id="ff515-111">**Git** ' e ve ardından **Başvuru Ekle**' ye basın.</span><span class="sxs-lookup"><span data-stu-id="ff515-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="ff515-112">Ardından, Web hizmeti yöntemini çağırır ve uygun denetimin veya pencerenin <xref:System.Windows.FrameworkElement.DataContext%2A> döndürülen nesneye ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="ff515-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="ff515-113">MTPS hizmetinin `GetContent` yöntemi `getContentRequest` nesnesine bir başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="ff515-113">The `GetContent` method of the MTPS service takes a reference to the `getContentRequest` object.</span></span> <span data-ttu-id="ff515-114">Bu nedenle, aşağıdaki örnek önce bir istek nesnesi ayarlar:</span><span class="sxs-lookup"><span data-stu-id="ff515-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="ff515-115"><xref:System.Windows.FrameworkElement.DataContext%2A> ayarlandıktan sonra, <xref:System.Windows.FrameworkElement.DataContext%2A> ayarlandığı nesnenin özelliklerine bağlar oluşturabilirsiniz...</span><span class="sxs-lookup"><span data-stu-id="ff515-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="ff515-116">Bu örnekte <xref:System.Windows.FrameworkElement.DataContext%2A>, `GetContent` yöntemi tarafından döndürülen `getContentResponse` nesnesine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ff515-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the `getContentResponse` object returned by the `GetContent` method.</span></span> <span data-ttu-id="ff515-117">Aşağıdaki örnekte <xref:System.Windows.Controls.ItemsControl> ' a bağlanır ve `getContentResponse``availableVersionsAndLocales` `locale` değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ff515-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the `locale` values of `availableVersionsAndLocales` of `getContentResponse`.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="ff515-118">`getContentResponse`yapısı hakkında daha fazla bilgi için bkz. [Içerik hizmeti belgeleri](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span><span class="sxs-lookup"><span data-stu-id="ff515-118">For information about the structure of `getContentResponse`, see [Content Service documentation](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff515-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff515-119">See also</span></span>

- [<span data-ttu-id="ff515-120">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ff515-120">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="ff515-121">Bağlama Kaynaklarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ff515-121">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="ff515-122">XAML'de Bağlama için Veriyi Kullanılabilir Yapma</span><span class="sxs-lookup"><span data-stu-id="ff515-122">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
