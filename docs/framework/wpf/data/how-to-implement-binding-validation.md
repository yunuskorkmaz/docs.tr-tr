---
title: 'Nasıl yapılır: Bağlama Doğrulaması Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 7a1a8df78a785066992472c7de37f958ae3467f1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920162"
---
# <a name="how-to-implement-binding-validation"></a>Nasıl yapılır: Bağlama Doğrulaması Uygulama

Bu örnek, bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ve stil tetikleyicisinin bir özel doğrulama kuralına göre geçersiz bir değer girildiğinde kullanıcıya bilgilendirmek için görsel geribildirim sağlamak üzere nasıl kullanılacağını gösterir.

## <a name="example"></a>Örnek

Aşağıdaki örnekteki <xref:System.Windows.Controls.TextBox> metin içeriği, `ods`adlı bir bağlama kaynak nesnesinin `Age` özelliğine (int türünde) bağlanır. Bağlama, Kullanıcı sayısal olmayan karakterler veya 130 21 ' den daha küçük bir değer girerse `AgeRangeRule` adlı bir doğrulama kuralı kullanmak üzere ayarlanır; Bu durumda, metin kutusunun yanında kırmızı bir ünlem işareti görünür ve hata iletisi  Kullanıcı fareyi metin kutusunun üzerine taşıdıkça.

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

Aşağıdaki örnek, <xref:System.Windows.Controls.ValidationRule> devralan `AgeRangeRule`uygulamasını gösterir ve <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemini geçersiz kılar. `Int32.Parse` yöntemi, geçersiz karakter içermediğinden emin olmak için değer üzerinde çağrılır. <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi, değerin ayrıştırma sırasında yakalanıp yakalanmadığını ve yaş değerinin alt ve üst sınırların dışında olup olmadığına bağlı olarak değerin geçerli olup olmadığını belirten bir <xref:System.Windows.Controls.ValidationResult> döndürür.

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

Aşağıdaki örnek, kullanıcıya doğrulama hatası bildirmek için kırmızı bir ünlem işareti oluşturan özel <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` gösterir. Denetim şablonları, bir denetimin görünümünü yeniden tanımlamak için kullanılır.

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

Aşağıdaki örnekte gösterildiği gibi, hata iletisini gösteren <xref:System.Windows.Controls.ToolTip> `textBoxInError`adlı stil kullanılarak oluşturulur. <xref:System.Windows.Controls.Validation.HasError%2A> değeri `true`, tetikleyici geçerli <xref:System.Windows.Controls.TextBox> araç ipucunu ilk doğrulama hatasına ayarlar. <xref:System.Windows.Data.Binding.RelativeSource%2A>, geçerli öğeye başvuran <xref:System.Windows.Data.RelativeSourceMode.Self>olarak ayarlanır.

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

Tüm örnek için bkz. [bağlama doğrulama örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).
  
Özel bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> sağlamazsanız, doğrulama hatası olduğunda kullanıcıya görsel geri bildirim sağlamak için varsayılan hata şablonunun göründüğünü unutmayın. Daha fazla bilgi için [veri bağlamaya genel bakış](data-binding-overview.md) bölümüne bakın. Ayrıca, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağlama kaynağı özelliğinin güncelleştirilmesi sırasında oluşturulan özel durumları yakalayan yerleşik bir doğrulama kuralı sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.ExceptionValidationRule>.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
