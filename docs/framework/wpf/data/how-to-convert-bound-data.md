---
title: "Nasıl yapılır: Bağımlı Veri Dönüştürme"
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
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f4bcde15940e76e1d022658e32ff6ef8676e45e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-convert-bound-data"></a>Nasıl yapılır: Bağımlı Veri Dönüştürme
Bu örnek nasıl bağlantılarında kullanılan veri dönüştürme uygulanacağını gösterir.  
  
 Veri bağlama sırasında dönüştürmek için uygulayan bir sınıf oluşturun <xref:System.Windows.Data.IValueConverter> içeren arabirimi <xref:System.Windows.Data.IValueConverter.Convert%2A> ve <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> yöntemleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, böylece yalnızca yıl, ay ve gün gösterir geçilen tarih değeri dönüştüren tarih dönüştürücü uygulamasını gösterir. Uygularken <xref:System.Windows.Data.IValueConverter> arabirimi, bir uygulama ile işaretleme iyi bir uygulama olan bir <xref:System.Windows.Data.ValueConversionAttribute> geliştirme belirtmek için öznitelik araçları aşağıdaki örnekteki gibi dönüştürme dahil edilen veri türleri:  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 Bir dönüştürücü oluşturduktan sonra onu bir kaynak olarak ekleyebilirsiniz, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya. Aşağıdaki örnekte, *src* eşler, ad alanına *DateConverter* tanımlanır.  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 Son olarak, aşağıdaki sözdizimini kullanarak, bağlama dönüştürücü kullanabilirsiniz. Aşağıdaki örnekte, metin içeriği <xref:System.Windows.Controls.TextBlock> bağlı *StartDate*, dış veri kaynağına özelliğinin olduğu.  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 Yukarıdaki örnekte başvurulan stil kaynakları, bu konuda gösterilmeyen kaynak bölümünde tanımlanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlama Doğrulaması Uygulama](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
