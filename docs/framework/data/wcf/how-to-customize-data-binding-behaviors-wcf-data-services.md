---
title: "Nasıl yapılır: veri davranışları (WCF Veri Hizmetleri) bağlama özelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ee72c905ab6df222d256eeeeb2a59579e82923b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Nasıl yapılır: veri davranışları (WCF Veri Hizmetleri) bağlama özelleştirme
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], tarafından çağrılır Özel mantık sağlayabilir <xref:System.Data.Services.Client.DataServiceCollection%601> ne zaman bir nesne eklenemez veya bağlama koleksiyonundan veya özellik değişikliği algıladığında kaldırılamaz. Bu özel mantık olarak başvurulan yöntemi olarak sağlanan <xref:System.Func%602> değerini döndüren Temsilciler `false` zaman varsayılan davranışı hala gerçekleştirilmelidir özel yöntem tamamlandığında ve `true` sonraki zaman işlenmesi Olay durdurulması gerekir.  
  
 Bu konudaki örnekler özel yöntemler her ikisi için tedarik `entityChanged` ve `entityCollectionChanged` parametrelerinin <xref:System.Data.Services.Client.DataServiceCollection%601>. Bu konuda kullanımda Northwind örnek veri hizmeti örnekleri ve otomatik olarak oluşturulur istemci veri sınıfları hizmeti. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 XAML dosyası için aşağıdaki arka plan kod sayfası oluşturan bir <xref:System.Data.Services.Client.DataServiceCollection%601> bağlama koleksiyona bağlı verilere değişiklikler meydana geldiğinde, çağrılan özel yöntemleriyle. Zaman <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> olayı oluşur, sağlanan yöntemi, veri hizmetinden silinmesini bağlama koleksiyondan kaldırıldığı öğeyi önler. Zaman <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> olayı oluşur, `ShipDate` zaten gönderilen siparişler değişiklikleri duruma getirilmez emin olmak için değeri doğrulandı.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML önceki örnek pencere tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
