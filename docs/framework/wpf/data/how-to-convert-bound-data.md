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
ms.openlocfilehash: 526305f32280fb75e95538b9014c34c11ed8bffa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
