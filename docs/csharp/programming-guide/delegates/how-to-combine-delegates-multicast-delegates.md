---
title: Temsilcileri birleştirme (çok noktaya yayın temsilcileri)-C# Programlama Kılavuzu
description: Temsilcileri çok noktaya yayın temsilcileri oluşturmak için birleştirmeyi öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d23ea758c9da2c3399f5d98e81360cc250b428a1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302743"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a>Temsilcileri birleştirme (Çok Noktaya Yayın Temsilcileri) (C# Programlama Kılavuzu)
Bu örnek, çok noktaya yayın temsilcileri oluşturmayı gösterir. [Temsilci](../../language-reference/builtin-types/reference-types.md) nesnelerinin yararlı bir özelliği, işleç kullanılarak bir temsilci örneğine birden çok nesne atanabilmesini sağlar `+` . Çok noktaya yayın temsilcisi, atanan temsilcilerin bir listesini içerir. Çok noktaya yayın temsilcisi çağrıldığında, listedeki temsilcileri sırayla çağırır. Yalnızca aynı türde temsilciler birleştirilebilir.  
  
 `-`İşleci bir çok noktaya yayın temsilcisinden bir bileşen temsilcisini kaldırmak için kullanılabilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.MulticastDelegate>
- [C# Programlama Kılavuzu](../index.md)
- [Ekinlikler](../events/index.md)
