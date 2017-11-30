---
title: "Nasıl yapılır: Bağımlılık Özelliği için Meta Verileri Geçersiz Kılma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e7cb01c81b5fb24830cbe0cc39befbadaf4405e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a>Nasıl yapılır: Bağımlılık Özelliği için Meta Verileri Geçersiz Kılma
Bu örnek çağırarak devralınan bir sınıftan gelen varsayılan bağımlılık özelliği meta verileri geçersiz kılmak nasıl gösterir <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> yöntemi ve türe özgü meta veriler sağlar.  
  
## <a name="example"></a>Örnek  
 Tanımlayarak kendi <xref:System.Windows.PropertyMetadata>, bir sınıf kendi varsayılan değeri ve özellik sistem geri aramaları gibi bağımlılık özelliği davranışlarını tanımlayabilir. Pek çok bağımlılık özelliği sınıfları kendi kayıt işleminin bir parçası belirlenen varsayılan meta verilere zaten var. Bu parçası olan bağımlılık özellikleri içerir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]. Böylece meta veriler üzerinden değiştirilebilir özelliği özelliklerini herhangi bir alt kümesi özgü gereksinimler ile eşleşir, sınıf devralma üzerinden bağımlılık özelliğini devralan bir sınıf orijinal meta verileri geçersiz kılabilirsiniz.  
  
 Bağımlılık özelliği üzerinde meta verileri geçersiz kılma (özelliği kaydeden nesnelerin belirli örneklerini örneklenen süre karşılık gelir) özellik sistemi tarafından kullanımda yerleştirilmiş o özellik önce yapılmalıdır. Çağrılar <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> olarak kendisini sağlar türü statik oluşturucular içinde gerçekleştirilmelidir `forType` parametresinin <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>. Sahibi türünün örneklerini mevcut sonra meta verileri değiştirmeye çalışırsa, bu özel durumları oluşturmaz, ancak özellik sistemi içinde tutarsız davranışlara neden olur. Ayrıca, meta veriler yalnızca bir kez başına türü geçersiz kılınabilir. Aynı türde meta verilerini geçersiz kılmak için sonraki denemeler bir özel durum oluşturacak.  
  
 Aşağıdaki örnekte, özel bir sınıf `MyAdvancedStateControl` için sağlanan meta verileri geçersiz kılar `StateProperty` tarafından `MyAdvancedStateControl` yeni özellik meta verileri ile. Örneği için varsayılan değeri `StateProperty` artık `true` özelliği sorgulanan zaman yeni oluşturulan üzerinde `MyAdvancedStateControl` örneği.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.DependencyProperty>  
 [Bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
