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
ms.openlocfilehash: d61631949382c177000b85aa8f4e093c3532c7ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556841"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>Nasıl yapılır: Bağımlı Öğeler Listesine Göre Değer Üretme
<xref:System.Windows.Data.MultiBinding> Kaynak özelliklerinin bir listesi için bir bağlama hedef özelliği bağlamak ve sonra verilen girişleri bir değerle bağlamanıza olanak sağlar. Bu örnek nasıl kullanılacağı ortaya <xref:System.Windows.Data.MultiBinding>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `NameListData` koleksiyonuna başvuruyor `PersonName` iki özellikleri içeren nesneleri olan nesneleri `firstName` ve `lastName`. Aşağıdaki örnek üreten bir <xref:System.Windows.Controls.TextBlock> ilk ve son adlarıyla bir kişinin soyadını ilk gösterir.  
  
 [!code-xaml[MultiBinding#Resources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 Son adı ilk biçimi nasıl üretilen anlamak için bir uygulaması bakalım `NameConverter`:  
  
 [!code-csharp[MultiBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` uygulayan <xref:System.Windows.Data.IMultiValueConverter> arabirimi. `NameConverter` ayrı bağlantılardan değerleri alır ve bunları değerleri nesne dizisinin içinde depolar. Hangi sırayla <xref:System.Windows.Data.Binding> öğeleri görünür altında <xref:System.Windows.Data.MultiBinding> bu değerleri dizisinde depolanır sipariş bir öğedir. Değeri <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> özniteliği parametre bağımsız değişkeni tarafından başvurulan <xref:System.Windows.Data.MultiBinding.Converter%2A> parametrenin adı biçimlendirme belirlemek için bir anahtar gerçekleştirir yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağımlı Veri Dönüştürme](../../../../docs/framework/wpf/data/how-to-convert-bound-data.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
