---
title: 'Nasıl yapılır: Bağlama Doğrulaması Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 347e38ba036e5c1a716a9edb75572c1a49f99631
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556972"
---
# <a name="how-to-implement-binding-validation"></a>Nasıl yapılır: Bağlama Doğrulaması Uygulama
Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ve geçersiz bir değer girdiğinizde kullanıcıyı bilgilendirmek üzere görsel geribildirim sağlamak için bir stil tetikleyici dayalı özel bir doğrulama kuralı üzerinde.  
  
## <a name="example"></a>Örnek  
 Metin içeriği <xref:System.Windows.Controls.TextBox> aşağıdaki örnekte bağlı `Age` adlı bağlama kaynak nesnesi (int türü) özelliğinin `ods`. Adlı bir doğrulama kuralı kullanmak için bağlamayı ayarlamak `AgeRangeRule` böylece kullanıcı sayısal olmayan karakterler veya 21'den küçük veya 130'dan büyük bir değer girerse metin kutusunun yanında kırmızı bir ünlem işareti görünür ve Microsoft hata iletisiyle bir araç ipucu görünür n kullanıcı fare metin kutusunun üzerine taşır.  
  
 [!code-xaml[BindValidation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 Aşağıdaki örnek uygulamasını gösterir `AgeRangeRule`, devralan <xref:System.Windows.Controls.ValidationRule> ve geçersiz kılmalar <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi. Int32.Parse() yöntemi değeri geçersiz karakterler içermediğinden emin olmak için çağrılır. <xref:System.Windows.Controls.ValidationRule.Validate%2A> Yöntemi döndürür bir <xref:System.Windows.Controls.ValidationResult> özel bir durum Ayrıştırma sırasında olup olmadığını belirledi ve geçerlilik değerinin alt ve üst sınırların dışında olup göre değerinin geçerli olup olmadığını gösterir.  
  
 [!code-csharp[BindValidation#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 Aşağıdaki örnek, özel gösterir <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` bir doğrulama hatası kullanıcıya bildirmek için kırmızı bir ünlem işareti oluşturur. Denetim şablonları, denetimin görünümünü yeniden tanımlamak için kullanılır.  
  
 [!code-xaml[BindValidation#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 Aşağıdaki örnekte gösterildiği gibi <xref:System.Windows.Controls.ToolTip> gösteren hata iletisi adlı stil kullanılarak oluşturulan `textBoxInError`. Varsa değerini <xref:System.Windows.Controls.Validation.HasError%2A> olan `true`, araç ipucu geçerli tetikleyici ayarlar <xref:System.Windows.Controls.TextBox> için ilk doğrulama hatası. <xref:System.Windows.Data.Binding.RelativeSource%2A> Ayarlanır <xref:System.Windows.Data.RelativeSourceMode.Self>geçerli öğe başvuran.  
  
 [!code-xaml[BindValidation#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 Tam bir örnek için bkz: [bağlama doğrulama örnek](http://go.microsoft.com/fwlink/?LinkID=159972).  
  
 Özel bir sağlamazsanız unutmayın <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> bir doğrulama hatası olduğunda kullanıcıya görsel geribildirim sağlamak için varsayılan hata şablonu görüntülenir. "Veri doğrulama" bölümüne bakın [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md) daha fazla bilgi için. Ayrıca, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağlama kaynak özelliği güncelleştirme sırasında oluşturulan özel durumları yakalar yerleşik doğrulama kuralı sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.ExceptionValidationRule>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
