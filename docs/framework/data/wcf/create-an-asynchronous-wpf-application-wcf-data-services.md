---
title: 'Nasıl yapılır: zaman uyumsuz bir Windows Presentation Framework uygulaması oluşturma (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
ms.openlocfilehash: 67f6e27e4042e1cddbef8b99a2235e1a21d270d2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152748"
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
