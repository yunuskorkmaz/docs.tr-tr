---
title: 'Nasıl yapılır: Bir Yönteme Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 6cdad46fd6d9ef3bc4ce1a13fedb6ff1d639d93e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967849"
---
# <a name="how-to-bind-to-a-method"></a>Nasıl yapılır: Bir Yönteme Bağlama
Aşağıdaki örneği kullanarak bir yönteme bağlama işlemi gösterilmektedir <xref:System.Windows.Data.ObjectDataProvider>.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `TemperatureScale` yöntemi olan bir sınıfı `ConvertTemp`, iki parametre alır (biri `double` ve biri `enum` türü `TempType)` ve bir sıcaklık ölçek kümesinden verilen değere dönüştürür. Aşağıdaki örnekte, bir <xref:System.Windows.Data.ObjectDataProvider> örneği oluşturmak için kullanılan `TemperatureScale` nesne. `ConvertTemp` İki belirtilen parametrelerle yöntemi çağrılır.  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 Yöntemi bir kaynak olarak kullanılabilir, sonuçlarını bağlayabilirsiniz. Aşağıdaki örnekte, <xref:System.Windows.Controls.TextBox.Text%2A> özelliği <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> , <xref:System.Windows.Controls.ComboBox> iki yöntemin parametrelerine bağlı. Bu, kullanıcıların dönüştürmek için sıcaklık belirtin ve dönüştürmek için sıcaklık ölçek sağlar. Unutmayın <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> ayarlanır `true` bağlıyoruz çünkü <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> özelliği <xref:System.Windows.Data.ObjectDataProvider> örneği ve özellikleri tarafından Sarmalanan nesnenin <xref:System.Windows.Data.ObjectDataProvider> ( `TemperatureScale` nesne).  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> Son <xref:System.Windows.Controls.Label> güncelleştirmeleri kullanıcı içeriğini değiştirdiğinde <xref:System.Windows.Controls.TextBox> veya seçimini <xref:System.Windows.Controls.ComboBox>.  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 Dönüştürücü `DoubleToString` çift alır ve bir dize dönüştürür <xref:System.Windows.Data.IValueConverter.Convert%2A> yönü (bağlama hedefi bağlama kaynağından olduğu <xref:System.Windows.Controls.TextBox.Text%2A> özelliği) ve dönüştüren bir `string` için bir `double` içinde <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> yönü.  
  
 `InvalidationCharacterRule` Olduğu bir <xref:System.Windows.Controls.ValidationRule> geçersiz karakterler için denetler. Kırmızı bir kenarlık olan varsayılan hata şablonu çevresinde <xref:System.Windows.Controls.TextBox>, giriş değeri bir çift değer olmadığında kullanıcıları bilgilendirmek için görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
- [Sabit Listesine Bağlama](how-to-bind-to-an-enumeration.md)
