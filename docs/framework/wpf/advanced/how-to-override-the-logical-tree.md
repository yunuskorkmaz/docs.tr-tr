---
title: 'Nasıl yapılır: Mantıksal Ağacı Geçersiz Kılma'
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: bf3459fff1a90326794d6713dd39c73596b0e960
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375235"
---
# <a name="how-to-override-the-logical-tree"></a>Nasıl yapılır: Mantıksal Ağacı Geçersiz Kılma
Çoğu durumda gerekli olmamasına karşın, Gelişmiş denetim yazarlarının mantıksal ağacı geçersiz kılma seçeneği vardır.  
  
## <a name="example"></a>Örnek  
 Bu örnek açıklar nasıl alt Sınıflama <xref:System.Windows.Controls.StackPanel> paneli yalnızca olabilir ve yalnızca tek bir alt öğe işleyecek bir davranışı zorlamak için mantıksal ağacı, bu durumda geçersiz kılma. Bu genellikle istenen bir davranış olmak zorunda değildir, ancak burada gösterilen öğenin normal mantıksal ağacı geçersiz kılma senaryoyu gösteren bir yolu olarak.  
  
 [!code-csharp[LogicalOverride#SingletonPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 Mantıksal ağacı hakkında daha fazla bilgi için bkz. [WPF içinde ağaçlar](trees-in-wpf.md).
