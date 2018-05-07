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
ms.openlocfilehash: 75d9d5b6981f868c7a172edd7f23cf923fedd525
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-to-a-web-service"></a>Nasıl yapılır: Web Hizmetine Bağlama
Bu örnek nasıl Web hizmeti yöntem çağrıları tarafından döndürülen nesne bağlanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte [MSDN ve TechNet yayımlama sistemi(MTPS) içerik hizmeti](http://go.microsoft.com/fwlink/?LinkId=95677) belirtilen belge tarafından desteklenen dillerin listesi alınamadı.  
  
 Bir Web hizmetini çağırmadan önce bir başvuru oluşturmanız gerekir. Kullanarak MTPS hizmetine Web başvurusu oluşturmak için [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], aşağıdaki adımları izleyin:  
  
1.  Projenizde açmak [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].  
  
2.  Gelen **proje** menüsünde tıklatın **Web Başvuru Ekle**.  
  
3.  İletişim kutusunda ayarlanan **URL** için [ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl ](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).  
  
4.  Tuşuna **Git** ve ardından **başvuru ekleme**.  
  
 Ardından, Web hizmeti yöntemi çağırın ve <xref:System.Windows.FrameworkElement.DataContext%2A> uygun denetim veya döndürülen nesne penceresine. **GetContent** yöntemi MTPS hizmetinin başvuru alır **getContentRequest** nesnesi. Bu nedenle, aşağıdaki örnekte, ilk olarak istek nesnesini ayarlar:  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 Sonra <xref:System.Windows.FrameworkElement.DataContext%2A> , oluşturabilir nesnenin özelliklerini bağlamalar, ayarlanmadı <xref:System.Windows.FrameworkElement.DataContext%2A> ayarlanmış. Bu örnekte, <xref:System.Windows.FrameworkElement.DataContext%2A> ayarlanır **getContentResponse** tarafından döndürülen nesne **GetContent** yöntemi. Aşağıdaki örnekte, <xref:System.Windows.Controls.ItemsControl> bağlar ve görüntüler **yerel ayar** değerlerini **availableVersionsAndLocales** , **getContentResponse**.  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 Yapısı hakkında bilgi için **getContentResponse**, bkz: [içerik hizmeti belgeleri](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Bağlama Kaynaklarına Genel Bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [XAML'de Bağlama için Veriyi Kullanılabilir Yapma](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
