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
ms.openlocfilehash: da183a34eb85de54b1e3f54f8d14c09e25640165
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459698"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>Nasıl yapılır: Bağımlı Öğeler Listesine Göre Değer Üretme
<xref:System.Windows.Data.MultiBinding>, bir bağlama hedefi özelliğini kaynak Özellikler listesine bağlamanıza olanak tanır ve ardından belirtilen girdilerle bir değer üretmek için mantık uygulayabilir. Bu örnek <xref:System.Windows.Data.MultiBinding>nasıl kullanacağınızı gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `NameListData`, `firstName` ve `lastName`iki özellik içeren nesneler olan `PersonName` nesneleri koleksiyonunu ifade eder. Aşağıdaki örnek, ilk adı en başta olan bir kişinin ilk ve son adlarını gösteren bir <xref:System.Windows.Controls.TextBlock> üretir.  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 Son ad-ilk biçiminin nasıl üretildiğini anlamak için `NameConverter`uygulamasına göz atalım:  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` <xref:System.Windows.Data.IMultiValueConverter> arabirimini uygular. `NameConverter`, bireysel bağlamalardan değerleri alır ve değerler nesne dizisinde depolar. <xref:System.Windows.Data.Binding> öğelerinin <xref:System.Windows.Data.MultiBinding> öğesi altında göründüğü sıra, bu değerlerin dizide depolanma sıradır. <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> özniteliğin değeri, <xref:System.Windows.Data.MultiBinding.Converter%2A> yönteminin parametre bağımsız değişkeni tarafından başvurulur, bu da adın nasıl biçimlendirileceğini belirleyen parametreyi bir anahtar gerçekleştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlı Veri Dönüştürme](how-to-convert-bound-data.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
