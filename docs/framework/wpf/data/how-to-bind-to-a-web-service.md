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
ms.openlocfilehash: 0a738d52cfb01fff1cb21d0e6ebb8f1b7b28d57f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695773"
---
# <a name="how-to-bind-to-a-web-service"></a>Nasıl yapılır: Web Hizmetine Bağlama
Bu örnekte, Web hizmeti yöntem çağrıları tarafından döndürülen nesnelere bağlama gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte [MSDN/TechNet yayımlama sistemi(MTPS) içerik hizmeti](https://go.microsoft.com/fwlink/?LinkId=95677) belirtilen bir belge tarafından desteklenen dillerin listesini almak için.  
  
 Bir Web hizmeti çağırmadan önce buna bir başvuru oluşturmanız gerekir. MTPS hizmeti kullanarak bir Web başvurusu [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], aşağıdaki adımları izleyin:  
  
1.  İçerisinde projenizi açın [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].  
  
2.  Gelen **proje** menüsünde tıklatın **Web başvurusu Ekle'yi**.  
  
3.  İletişim kutusunda ayarlanan **URL** için [ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl ](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).  
  
4.  Tuşuna **Git** ardından **Başvurusu Ekle**.  
  
 Ardından, Web hizmeti yöntemi çağırmanızı ve <xref:System.Windows.FrameworkElement.DataContext%2A> uygun denetim ya da penceresine döndürülen nesne. **GetContent** MTPS hizmetinin yöntemi, bir başvuru alır **getContentRequest** nesne. Bu nedenle, aşağıdaki örnekte, ilk olarak istek nesnesini ayarlar:  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 Sonra <xref:System.Windows.FrameworkElement.DataContext%2A> , oluşturabilir nesnenin özelliklerini bağlar, ayarlanmadı <xref:System.Windows.FrameworkElement.DataContext%2A> ayarlanmış. Bu örnekte, <xref:System.Windows.FrameworkElement.DataContext%2A> ayarlanır **getContentResponse** tarafından döndürülen nesne **GetContent** yöntemi. Aşağıdaki örnekte, <xref:System.Windows.Controls.ItemsControl> bağlar ve görüntüler **yerel** değerlerini **availableVersionsAndLocales** , **getContentResponse**.  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 Yapısı hakkında bilgi için **getContentResponse**, bkz: [içerik hizmeti belgeleri](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Bağlama Kaynaklarına Genel Bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md)
- [XAML'de Bağlama için Veriyi Kullanılabilir Yapma](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
