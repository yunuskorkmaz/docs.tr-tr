---
title: 'Nasıl yapılır: Veri bağlama davranışlarını özelleştirme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: c878096cba7d31e0b48727213ee1bb8239b8f690
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790755"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Nasıl yapılır: Veri bağlama davranışlarını özelleştirme (WCF Veri Hizmetleri)
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], bağlama koleksiyonuna bir nesne eklendiğinde veya kaldırıldığında ya da bir <xref:System.Data.Services.Client.DataServiceCollection%601> özellik değişikliği algılandığında tarafından çağrılan özel mantık sağlayabilirsiniz. Bu özel mantık, temsilci olarak <xref:System.Func%602> başvurulan yöntemler olarak, özel yöntem tamamlandığında ve `true` sonraki işlem tamamlandığında `false` , varsayılan davranışın ne zaman gerçekleştirilmesi gerektiğini belirten bir değer döndürür. olay durdurulmalıdır.  
  
 Bu konudaki örnekler, `entityChanged` ve `entityCollectionChanged` parametreleri <xref:System.Data.Services.Client.DataServiceCollection%601>için özel yöntemler sağlar. Bu konudaki örneklerde, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıfları kullanılır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 XAML dosyası için aşağıdaki arka plan kod sayfası, bağlama koleksiyonuna bağlanan <xref:System.Data.Services.Client.DataServiceCollection%601> verilerde değişiklik olduğunda çağrılan özel yöntemlerle birlikte oluşturur. <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> Olay gerçekleştiğinde, sağlanan yöntem, bağlama koleksiyonundan kaldırılmış bir öğenin veri hizmetinden silinmesini engeller. <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> Olay gerçekleştiğinde`ShipDate` değer, zaten sevk edilen siparişlerde değişiklik yapılmadığından emin olmak için onaylanır.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML, önceki örneğe ait pencereyi tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
