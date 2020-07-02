---
title: 'Nasıl yapılır: Basit bir Bağlama Oluşturma'
description: Windows Presentation Foundation (WPF) içinde bu nasıl yapılır örneği aracılığıyla uygulamalarınız için basit bir bağlama oluşturun.
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 63dc44b442bb4658382bf12faf57b51c8e0698bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618707"
---
# <a name="how-to-create-a-simple-binding"></a>Nasıl yapılır: Basit bir Bağlama Oluşturma
Bu örnekte, nasıl basit bir şekilde oluşturabileceğiniz gösterilmektedir <xref:System.Windows.Data.Binding> .  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bir `Person` String özelliği adlı bir nesneniz vardır `PersonName` . `Person`Nesnesi, adlı ad alanında tanımlanır `SDKSample` .  
  
 Aşağıdaki örnekteki öğesini içeren vurgulanmış çizgi, `<src>` `Person` bir özellik değeri olan nesnesini başlatır `PersonName` `Joe` . Bu, `Resources` bölümünde yapılır ve atanır `x:Key` .  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Öğesini içeren vurgulanmış çizgi, `<TextBlock>` daha sonra <xref:System.Windows.Controls.TextBlock> denetimi `PersonName` özelliğine bağlar. Sonuç olarak, <xref:System.Windows.Controls.TextBlock> "ali" değeri ile görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
