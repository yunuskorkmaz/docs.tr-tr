---
title: 'Nasıl yapılır: zaman uyumsuz Windows Presentation Framework uygulama (WCF Veri Hizmetleri) oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
ms.openlocfilehash: d6acf3cbbfce491ebf98513b116d76ef9feb6d08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357640"
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a>Nasıl yapılır: zaman uyumsuz Windows Presentation Framework uygulama (WCF Veri Hizmetleri) oluşturma
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], bir Windows Presentation Framework (WPF) uygulama kullanıcı Arabirimi öğesi için bir veri hizmetinden alınan veriler bağlayabilirsiniz. Daha fazla bilgi için bkz: [denetimlere veri bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md). Uygulama veri hizmet isteğine yanıt beklenirken yanıt vermeye devam sağlar zaman uyumsuz bir şekilde veri hizmeti karşı işlemleri de çalıştırabilirsiniz. Silverlight uygulamaları, veri hizmeti zaman uyumsuz olarak erişmek için gereklidir. Daha fazla bilgi için bkz: [zaman uyumsuz işlemleri](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
 Bu konuda, bir veri hizmeti zaman uyumsuz olarak erişmek ve sonuçları WPF uygulaması öğelerine bağlama gösterilmektedir. Bu konuda kullanımda Northwind örnek veri hizmeti örnekleri ve otomatik olarak oluşturulur istemci veri sınıfları hizmeti. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML WPF uygulaması penceresini tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## <a name="example"></a>Örnek  
 XAML dosyası için aşağıdaki arka plan kod sayfasını veri hizmeti kullanarak zaman uyumsuz bir sorguyu çalıştırır ve sonuçları WPF penceresi öğelerine bağlar.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
