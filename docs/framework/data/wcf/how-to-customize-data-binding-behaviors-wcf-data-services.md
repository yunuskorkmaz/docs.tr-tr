---
title: 'Nasıl yapılır: veri bağlama davranışlarını özelleştirme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: 453562dd1b86756bf9fc1684dc649dba1c24c578
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569171"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Nasıl yapılır: veri bağlama davranışlarını özelleştirme (WCF Veri Hizmetleri)
WCF Veri Hizmetleri, bağlama koleksiyonuna bir nesne eklendiğinde veya kaldırıldığında ya da bir özellik değişikliği algılandığında, <xref:System.Data.Services.Client.DataServiceCollection%601> tarafından çağrılan özel mantık sağlayabilirsiniz. Bu özel mantık, bir `false` değeri döndüren <xref:System.Func%602> temsilciler olarak başvurulan yöntemler olarak sağlanır. Bu, varsayılan davranış tamamlandığında, olayın sonraki işlenmesi durumunda `true`, yine de gerçekleştirilmeli.  
  
 Bu konudaki örneklerde, <xref:System.Data.Services.Client.DataServiceCollection%601>`entityChanged` ve `entityCollectionChanged` parametreleri için özel yöntemler verilmektedir. Bu konudaki örneklerde, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıfları kullanılır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 XAML dosyası için aşağıdaki arka plan kod sayfası, bağlama koleksiyonuna bağlanan verilerde değişiklikler olduğunda çağrılan özel yöntemlerle bir <xref:System.Data.Services.Client.DataServiceCollection%601> oluşturur. <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> olayı gerçekleştiğinde, sağlanan yöntem, bağlama koleksiyonundan kaldırılmış bir öğenin veri hizmetinden silinmesini engeller. <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> olayı gerçekleştiğinde, zaten sevk edilen siparişlerde değişiklik yapılmadığından emin olmak için `ShipDate` değeri onaylanır.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML, önceki örneğe ait pencereyi tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
