---
title: 'Nasıl yapılır: zaman uyumsuz bir Windows Presentation Framework uygulaması oluşturma (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
ms.openlocfilehash: 9bc1cef1f76e6e55e9cd5ed318741f8913abbaab
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569274"
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a>Nasıl yapılır: zaman uyumsuz bir Windows Presentation Framework uygulaması oluşturma (WCF Veri Hizmetleri)
WCF Veri Hizmetleri, bir veri hizmetinden alınan verileri bir Windows Presentation Framework (WPF) uygulamasının UI öğesine bağlayabilirsiniz. Daha fazla bilgi için bkz. [verileri denetimlere bağlama](binding-data-to-controls-wcf-data-services.md). Ayrıca, bir veri hizmeti isteğine yanıt beklerken uygulamanın yanıt vermeye devam etmesine olanak tanıyan, veri hizmetine karşı işlemleri zaman uyumsuz bir şekilde yürütebilirsiniz. Veri hizmetine zaman uyumsuz olarak erişmek için Silverlight uygulamaları gerekir. Daha fazla bilgi için bkz. [zaman uyumsuz işlemler](asynchronous-operations-wcf-data-services.md).  
  
 Bu konu, bir veri hizmetine zaman uyumsuz olarak nasıl erişebileceğiniz ve sonuçları WPF uygulamasının öğelerine nasıl bağlayacağınız gösterilmektedir. Bu konudaki örneklerde, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıfları kullanılır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML WPF uygulamasının penceresini tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## <a name="example"></a>Örnek  
 XAML dosyası için aşağıdaki arka plan kod sayfası, veri hizmetini kullanarak zaman uyumsuz bir sorgu yürütür ve sonuçları WPF penceresindeki öğelere bağlar.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
