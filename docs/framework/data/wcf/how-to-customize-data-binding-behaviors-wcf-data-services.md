---
title: 'Nasıl yapılır: Veri bağlama davranışlarını (WCF Veri Hizmetleri) özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: f55c9790b8300a1a3f26e031a17a0982638b562b
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517427"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Nasıl yapılır: Veri bağlama davranışlarını (WCF Veri Hizmetleri) özelleştirme
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], çağıran özel mantığı sağlayabilirsiniz <xref:System.Data.Services.Client.DataServiceCollection%601> ne zaman bir nesne eklendiğinde veya bağlama koleksiyondan veya bir özellik değişiminin algılandığında kaldırıldı. Bu özel mantıksal olarak başvurulan yöntemleri olarak sağlanan <xref:System.Func%602> değerini döndüren bir temsilci `false` olduğunda varsayılan davranışı hala gerçekleştirilmelidir özel yöntem tamamlandığında ve `true` sonraki zaman işlenmesi Olay durdurulması gerekir.  
  
 Bu konudaki örnekleri her ikisi için özel yöntemler sağlamak `entityChanged` ve `entityCollectionChanged` parametrelerinin <xref:System.Data.Services.Client.DataServiceCollection%601>. Otomatik olarak oluşturulan istemci verilerinin ve bu konuda kullanım Northwind örnek veri hizmeti sınıfları hizmeti. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 XAML dosyası için aşağıdaki arka plan kod sayfası oluşturan bir <xref:System.Data.Services.Client.DataServiceCollection%601> bağlama koleksiyonuna bağlı veri değişiklikler meydana geldiğinde çağrılan yöntemlere özel ile. Zaman <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> bir olay oluşursa, sağlanan yöntem veri hizmetinden silinmesini bağlama koleksiyondan kaldırılmış bir öğe engeller. Zaman <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> bir olay oluşursa, `ShipDate` değeri değişiklikler için zaten sipariş tasarlanmamış olan emin olmak için doğrulandı.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML, önceki örnek penceresini tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
