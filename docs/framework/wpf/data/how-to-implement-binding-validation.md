---
title: 'Nasıl yapılır: Bağlama Doğrulaması Uygulama'
description: Windows Presentation Foundation (WPF) içinde geçersiz bir değer girildiğinde kullanıcıya görsel geri bildirim sağlamak için bağlama doğrulaması kullanmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 0813be9f79a83a9dae26db1dadb58b5e973339fd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617888"
---
# <a name="how-to-implement-binding-validation"></a>Nasıl yapılır: Bağlama Doğrulaması Uygulama

Bu örnek <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> , bir özel doğrulama kuralına bağlı olarak geçersiz bir değer girildiğinde kullanıcıya bilgilendirmek için görsel geribildirim sağlamak üzere bir ve stil tetikleyicisinin nasıl kullanılacağını gösterir.

## <a name="example"></a>Örnek

Aşağıdaki örnekteki öğesinin metin içeriği <xref:System.Windows.Controls.TextBox> `Age` adlı bir bağlama kaynak nesnesinin özelliğine (int türünde) bağlanır `ods` . Bağlama, `AgeRangeRule` Kullanıcı sayısal olmayan karakterler veya 21 ' den daha küçük bir değer girerse veya 130 ' den büyük bir değer girerse, metin kutusunun yanında kırmızı bir ünlem işareti ve Kullanıcı fareyi metin kutusunun üzerine taşırken hata iletisiyle birlikte bir araç ipucu görünür.

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

Aşağıdaki örnek `AgeRangeRule` , öğesinden devralan <xref:System.Windows.Controls.ValidationRule> ve geçersiz kılacak öğesinin uygulamasını gösterir <xref:System.Windows.Controls.ValidationRule.Validate%2A> . `Int32.Parse`Yöntemi, geçersiz karakter içermediğinden emin olmak için değer üzerinde çağrılır. <xref:System.Windows.Controls.ValidationRule.Validate%2A>Yöntemi, bir <xref:System.Windows.Controls.ValidationResult> özel durumun ayrıştırma sırasında yakalanıp yakalanmadığını ve yaş değerinin alt ve üst sınırların dışında olup olmadığına bağlı olarak değerin geçerli olup olmadığını belirten bir döndürür.

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

Aşağıdaki örnek, <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` kullanıcıya doğrulama hatası bildirmek için kırmızı bir ünlem işareti oluşturan özel bir gösterir. Denetim şablonları, bir denetimin görünümünü yeniden tanımlamak için kullanılır.

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

Aşağıdaki örnekte gösterildiği gibi, <xref:System.Windows.Controls.ToolTip> hata iletisini gösteren adlı stil kullanılarak oluşturulur `textBoxInError` . Değeri <xref:System.Windows.Controls.Validation.HasError%2A> ise `true` , tetikleyici geçerli olan araç ipucunu <xref:System.Windows.Controls.TextBox> ilk doğrulama hatasına ayarlar. , <xref:System.Windows.Data.Binding.RelativeSource%2A> <xref:System.Windows.Data.RelativeSourceMode.Self> Geçerli öğeye başvuran olarak ayarlanır.

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

Tüm örnek için bkz. [bağlama doğrulama örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).
  
Özel bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> doğrulama hatası olduğunda kullanıcıya görsel geri bildirim sağlamak için, özel bir hata şablonu sunmayacağınızı unutmayın. Daha fazla bilgi için [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md) bölümüne bakın. Ayrıca, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağlama kaynağı özelliğinin güncelleştirilmesi sırasında oluşturulan özel durumları yakalayan yerleşik bir doğrulama kuralı sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.ExceptionValidationRule>.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
