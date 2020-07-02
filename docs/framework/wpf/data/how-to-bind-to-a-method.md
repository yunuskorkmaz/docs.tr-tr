---
title: 'Nasıl yapılır: Bir Yönteme Bağlama'
description: Windows Presentation Foundation (WPF) içindeki bir nesnenin yöntemine nasıl bağlanılacağını öğrenmek için bu örneği izleyin.
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 9501e6357203c21651e85f1d65059be1d70becf2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619604"
---
# <a name="how-to-bind-to-a-method"></a>Nasıl yapılır: Bir Yönteme Bağlama
Aşağıdaki örnek kullanarak bir yöntemine nasıl bağlanılacağını gösterir <xref:System.Windows.Data.ObjectDataProvider> .  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `TemperatureScale` `ConvertTemp` iki parametre (biri ve türden biri) alan `double` `enum` `TempType)` ve verilen değeri bir sıcaklık ölçeğinden diğerine dönüştüren bir yöntemi olan bir sınıftır. Aşağıdaki örnekte, <xref:System.Windows.Data.ObjectDataProvider> nesnesinin örneğini oluşturmak için kullanılır `TemperatureScale` . `ConvertTemp`Yöntemi belirtilen iki parametreyle çağrılır.  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 Artık Yöntem bir kaynak olarak kullanılabilir olduğuna göre, sonuçlarına bağlanabilir. Aşağıdaki örnekte, öğesinin ve öğesinin <xref:System.Windows.Controls.TextBox.Text%2A> özelliği <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> <xref:System.Windows.Controls.ComboBox> yönteminin iki parametresine bağlanır. Bu, kullanıcıların dönüştürülecek sıcaklığı ve sıcaklık ölçeğini ' den belirtmesini sağlar. <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>Öğesinin `true` <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> <xref:System.Windows.Data.ObjectDataProvider> , <xref:System.Windows.Data.ObjectDataProvider> (nesnesi) tarafından Sarmalanan nesnenin özelliklerini değil, örneğinin özelliğine bağladığımızda olarak ayarlandığını unutmayın `TemperatureScale` .  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.Label> Kullanıcı veya seçiminin içeriğini değiştirdiğinde son güncelleştirmelerin ' i <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.ComboBox> .  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 Dönüştürücü `DoubleToString` bir Double alır ve yöndeki bir dizeye dönüştürür <xref:System.Windows.Data.IValueConverter.Convert%2A> (bağlama kaynağından bağlama hedefi, <xref:System.Windows.Controls.TextBox.Text%2A> özelliği olan) ve `string` yönünde öğesine dönüştürür `double` <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> .  
  
 `InvalidationCharacterRule` <xref:System.Windows.Controls.ValidationRule> Geçersiz karakterleri denetleyen bir. ' In etrafında kırmızı bir kenarlık olan varsayılan hata şablonu, <xref:System.Windows.Controls.TextBox> giriş değeri bir Double değeri olmadığında kullanıcılara bildirimde bulunur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
- [Sabit listesine bağlama](how-to-bind-to-an-enumeration.md)
