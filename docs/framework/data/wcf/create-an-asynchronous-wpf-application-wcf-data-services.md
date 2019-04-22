---
title: 'Nasıl yapılır: Bir zaman uyumsuz Windows Presentation Framework uygulaması (WCF Veri Hizmetleri) oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
ms.openlocfilehash: c5dc4e34711cdb128eb012633bad104d0060be71
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517063"
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a>Nasıl yapılır: Bir zaman uyumsuz Windows Presentation Framework uygulaması (WCF Veri Hizmetleri) oluşturma
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], bir Windows Presentation Framework (WPF) uygulamasının kullanıcı Arabirimi öğesi için bir veri hizmetinden alınan verileri bağlayabilirsiniz. Daha fazla bilgi için [denetimlere veri bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md). Veri Hizmeti üzerinde işlemler için veri hizmeti isteği bir yanıt beklerken yanıt vermeye devam uygulamanın sağlar zaman uyumsuz olarak yürütebilirsiniz. Silverlight uygulamaları, veri hizmetini zaman uyumsuz olarak erişmek için gereklidir. Daha fazla bilgi için [zaman uyumsuz işlemler](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
 Bu konuda, zaman uyumsuz olarak bir veri hizmetine erişmek ve sonuçları bir WPF uygulamasını öğelerine bağlama gösterilmektedir. Otomatik olarak oluşturulan istemci verilerinin ve bu konuda kullanım Northwind örnek veri hizmeti sınıfları hizmeti. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML WPF uygulaması penceresini tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## <a name="example"></a>Örnek  
 XAML dosyası için aşağıdaki arka plan kod sayfası veri hizmetini kullanarak zaman uyumsuz sorgu çalıştırır ve sonuçları okno WPF öğelerine bağlar.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
