---
title: 'Nasıl yapılır: Bağımlı Veri Dönüştürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: 5069b6d6b7ded52011ec4c65ca2c47e41bba2ece
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705728"
---
# <a name="how-to-convert-bound-data"></a>Nasıl yapılır: Bağımlı Veri Dönüştürme
Bu örnek uygulama bağlamalarında kullanılan veri dönüştürme işlemini gösterir.  
  
 Veri bağlama sırasında dönüştürmek için uygulayan bir sınıf oluşturmanız <xref:System.Windows.Data.IValueConverter> içeren arabirimi <xref:System.Windows.Data.IValueConverter.Convert%2A> ve <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> yöntemleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, yıl, ay ve gün yalnızca gösterir böylece geçilen tarih değeri dönüştürür tarih dönüştürücü uygulanışı gösterilmektedir. Uygularken <xref:System.Windows.Data.IValueConverter> arabirimi, bir uygulama ile donatmak için iyi bir uygulama olan bir <xref:System.Windows.Data.ValueConversionAttribute> geliştirme belirtmek için özniteliği veri türlerini dönüştürme, aşağıdaki örnekte olduğu gibi ilgili araçları:  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 Bir dönüştürücü oluşturulduktan sonra bunu bir kaynak olarak ekleyebilirsiniz, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya. Aşağıdaki örnekte, *src* eşler, ad alanına *DateConverter* tanımlanır.  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 Son olarak, aşağıdaki sözdizimini kullanarak, bağlama dönüştürücüyü kullanabilirsiniz. Aşağıdaki örnekte, metin içeriği <xref:System.Windows.Controls.TextBlock> bağlı *StartDate*, bir dış veri kaynağının bir özelliği olan.  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 Yukarıdaki örnekte başvurulan stil kaynakları, bu konuda gösterilen olmayan bir kaynak bölümünde tanımlanır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bağlama Doğrulaması Uygulama](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)
- [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
