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
# <a name="how-to-bind-to-a-web-service"></a>Nasıl yapılır: Web Hizmetine Bağlama
Bu örnek, Web hizmeti yöntem çağrıları tarafından döndürülen nesnelere nasıl bağlanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, belirtilen bir belge tarafından desteklenen dillerin listesini almak için MSDN/TechNet yayımlama sistemi (MTPS) Içerik hizmetini kullanır.  
  
 Bir Web hizmetini çağırmak için bir başvuru oluşturmanız gerekir. Visual Studio kullanarak MTPS hizmetine bir Web başvurusu oluşturmak için aşağıdaki adımları izleyin:  
  
1. Projenizi Visual Studio 'da açın.  
  
2. **Proje** menüsünden **Web başvurusu Ekle**' ye tıklayın.  
  
3. İletişim kutusunda **URL 'yi** [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl)olarak ayarlayın.  
  
4. **Git** ' e ve ardından **Başvuru Ekle**' ye basın.  
  
 Ardından, Web hizmeti yöntemini çağırır ve uygun denetimin veya pencerenin <xref:System.Windows.FrameworkElement.DataContext%2A> döndürülen nesneye ayarlarsınız. MTPS hizmetinin `GetContent` yöntemi `getContentRequest` nesnesine bir başvuru alır. Bu nedenle, aşağıdaki örnek önce bir istek nesnesi ayarlar:  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <xref:System.Windows.FrameworkElement.DataContext%2A> ayarlandıktan sonra, <xref:System.Windows.FrameworkElement.DataContext%2A> ayarlandığı nesnenin özelliklerine bağlar oluşturabilirsiniz... Bu örnekte <xref:System.Windows.FrameworkElement.DataContext%2A>, `GetContent` yöntemi tarafından döndürülen `getContentResponse` nesnesine ayarlanır. Aşağıdaki örnekte <xref:System.Windows.Controls.ItemsControl> ' a bağlanır ve `getContentResponse``availableVersionsAndLocales` `locale` değerlerini görüntüler.  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 `getContentResponse`yapısı hakkında daha fazla bilgi için bkz. [Içerik hizmeti belgeleri](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Bağlama Kaynaklarına Genel Bakış](binding-sources-overview.md)
- [XAML'de Bağlama için Veriyi Kullanılabilir Yapma](how-to-make-data-available-for-binding-in-xaml.md)
