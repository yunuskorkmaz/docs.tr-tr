---
title: 'Nasıl yapılır: Bağımlı Öğeler Listesine Göre Değer Üretme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: c2ec5ff26c89649294df266e790445e5aa5d08ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200525"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>Nasıl yapılır: Bağımlı Öğeler Listesine Göre Değer Üretme
<xref:System.Windows.Data.MultiBinding> bir bağlama hedefi özelliği kaynak özellikleri listesine bağlayın ve sonra verilen girişleri bir değerle bağlamanıza olanak sağlar. Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Data.MultiBinding>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `NameListData` bir koleksiyonuna başvuruyor `PersonName` iki özellikleri içeren nesneleri olan nesneleri `firstName` ve `lastName`. Aşağıdaki örnek üreten bir <xref:System.Windows.Controls.TextBlock> ilk ve son adlarıyla bir kişinin soyadı ilk gösterir.  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 Son adı ilk biçiminin nasıl üretildiğini anlamak için bir uygulaması bakalım `NameConverter`:  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` uygulayan <xref:System.Windows.Data.IMultiValueConverter> arabirimi. `NameConverter` değerleri tek tek bağlamaları alır ve değerleri nesne dizide saklar. Bir sırayı <xref:System.Windows.Data.Binding> öğeleri görünür altında <xref:System.Windows.Data.MultiBinding> öğedir sırası dizideki değerleri depolanır. Değerini <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> özniteliği parametre bağımsız değişkeni tarafından başvurulan <xref:System.Windows.Data.MultiBinding.Converter%2A> parametrenin adını biçimlendirmek nasıl belirlemek için bir anahtar gerçekleştiren yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlı Veri Dönüştürme](how-to-convert-bound-data.md)
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
