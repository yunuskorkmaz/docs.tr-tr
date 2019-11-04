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
ms.openlocfilehash: f9ad390626092d481bf47f017f643a29302c1b29
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458862"
---
# <a name="how-to-convert-bound-data"></a>Nasıl yapılır: Bağımlı Veri Dönüştürme
Bu örnek, bağlamalarda kullanılan verilere dönüştürmenin nasıl uygulanacağını gösterir.  
  
 Bağlama sırasında verileri dönüştürmek için, <xref:System.Windows.Data.IValueConverter.Convert%2A> ve <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> yöntemlerini içeren <xref:System.Windows.Data.IValueConverter> arabirimini uygulayan bir sınıf oluşturmanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yalnızca yılı, ayı ve günü görüntüleyecek şekilde geçirilen tarih değerini dönüştüren bir tarih dönüştürücünün uygulamasını gösterir. <xref:System.Windows.Data.IValueConverter> arabirimini uygularken, aşağıdaki örnekte olduğu gibi, dönüştürme işleminde yer alan veri türleri için geliştirme araçlarına işaret eden bir <xref:System.Windows.Data.ValueConversionAttribute> özniteliğiyle uygulamayı süslemek iyi bir uygulamadır:  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 Dönüştürücüyü oluşturduktan sonra, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyanıza kaynak olarak ekleyebilirsiniz. Aşağıdaki örnekte, *src* , *DateConverter* 'ın tanımlandığı ad alanı ile eşlenir.  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 Son olarak, aşağıdaki sözdizimini kullanarak bağlamadaki dönüştürücüyü kullanabilirsiniz. Aşağıdaki örnekte <xref:System.Windows.Controls.TextBlock> metin içeriği, bir dış veri kaynağının özelliği olan *StartDate*' e bağlanır.  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 Yukarıdaki örnekte başvurulan stil kaynakları, bu konuda görünmeyen bir kaynak bölümünde tanımlanmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlama Doğrulaması Uygulama](how-to-implement-binding-validation.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
