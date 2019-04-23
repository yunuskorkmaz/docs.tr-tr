---
title: 'Nasıl yapılır: Bağlama Doğrulaması Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 3950df8b6f4b48a035c6ebf37d8d65c18cb82e1e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197223"
---
# <a name="how-to-implement-binding-validation"></a>Nasıl yapılır: Bağlama Doğrulaması Uygulama
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ve geçersiz bir değer girildiğinde, kullanıcıyı bilgilendirmek üzere görsel geri bildirim sağlamak için bir stil tetikleyicisi dayalı bir özel doğrulama kuralı.  
  
## <a name="example"></a>Örnek  
 Metin içeriği <xref:System.Windows.Controls.TextBox> aşağıdaki örnekte bağlı `Age` özelliği (int türü) adlı bir bağlama kaynağı nesnesinin `ods`. Adlı bir doğrulama kuralı kullanılacak bağlama ayarlayın `AgeRangeRule` kullanıcı sayısal olmayan karakterler veya 21'den küçük veya 130'dan büyük bir değer girerse metin kutusunun yanındaki kırmızı bir ünlem işareti görünür ve Microsoft hata iletisiyle bir araç ipucu görünür n kullanıcı, metin kutusunun üzerine fare taşır.  
  
 [!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 Aşağıdaki örnek uygulamasını gösterir `AgeRangeRule`, işlevinden devralan <xref:System.Windows.Controls.ValidationRule> ve geçersiz kılmaları <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi. Int32.Parse() yöntem, değeri geçersiz karakterler içermediğinden emin olmak için çağrılır. <xref:System.Windows.Controls.ValidationRule.Validate%2A> Yöntemi döndürür bir <xref:System.Windows.Controls.ValidationResult> Ayrıştırma sırasında bir özel durum olup yakalanır ve yaş değeri alt ve üst sınırları dışında olup temel değerin geçerli olup olmadığını gösterir.  
  
 [!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 Aşağıdaki örnek, özel gösterir <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` bir doğrulama hatası kullanıcıya bildirmek için kırmızı bir ünlem işareti oluşturur. Denetim şablonları, bir denetimin görünümünü yeniden tanımlamak için kullanılır.  
  
 [!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 Aşağıdaki örnekte gösterildiği gibi <xref:System.Windows.Controls.ToolTip> gösteren hata iletisi adlı stili kullanılarak oluşturulan `textBoxInError`. Varsa değerini <xref:System.Windows.Controls.Validation.HasError%2A> olduğu `true`, tetikleyici araç ipucu geçerli ayarlar <xref:System.Windows.Controls.TextBox> için ilk doğrulama hatası. <xref:System.Windows.Data.Binding.RelativeSource%2A> Ayarlanır <xref:System.Windows.Data.RelativeSourceMode.Self>, geçerli öğeye başvurma.  
  
 [!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 Tam bir örnek için bkz. [bağlama doğrulaması örnek](https://go.microsoft.com/fwlink/?LinkID=159972).  
  
 Özel bir sağlamazsanız unutmayın <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> bir doğrulama hatası olmadığında kullanıcıya görsel geribildirim sağlamak için varsayılan hata şablon görüntülenir. "Veri doğrulama" bölümüne bakın [Data Binding Overview](data-binding-overview.md) daha fazla bilgi için. Ayrıca, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağlama kaynak özelliği güncelleştirme sırasında oluşturulan özel durumları yakalayan bir yerleşik doğrulama kuralları sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.ExceptionValidationRule>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
