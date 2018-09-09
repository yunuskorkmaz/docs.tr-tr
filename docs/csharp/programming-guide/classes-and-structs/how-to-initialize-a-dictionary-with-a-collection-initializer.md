---
title: Nasıl (C# programlama Kılavuzu) koleksiyon Başlatıcısı ile bir sözlük başlatma
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: ca2f508e5500cc135b2712362bcfb71778a664c1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227343"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Nasıl (C# programlama Kılavuzu) koleksiyon Başlatıcısı ile bir sözlük başlatma

A <xref:System.Collections.Generic.Dictionary%602> anahtar/değer çiftleri koleksiyonu içerir. Kendi <xref:System.Collections.Generic.Dictionary%602.Add*> yöntemi biri anahtar ve değer için bir tane olmak üzere iki parametre alır. Başlatmak için bir <xref:System.Collections.Generic.Dictionary%602>, ya da herhangi bir koleksiyon olan `Add` yöntemi birden çok parametre alır, aşağıdaki örnekte gösterildiği gibi her parametre kümesi ayraçlarının içine alın.

## <a name="example"></a>Örnek

Aşağıdaki kod örneğinde, bir <xref:System.Collections.Generic.Dictionary%602> türünün bir örneğini ile başlatılmış `StudentName`.  
  
[!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]

Küme ayraçları içine koleksiyonun her öğesine iki çiftleri unutmayın. Nesne Başlatıcısı için en içteki ayraç içine `StudentName`, ve en dıştaki ayraç içine eklenecek anahtar/değer çifti için Başlatıcı `students` <xref:System.Collections.Generic.Dictionary%602>. Son olarak, tüm koleksiyon Başlatıcısı sözlüğü için parantez içine alınır.

## <a name="compiling-the-code"></a>Kod derleme

Bu kodu çalıştırmak için kopyalayın ve Visual Studio'da oluşturulan bir Visual C# konsol uygulaması projesi sınıfı yapıştırın. Varsayılan olarak, bu proje 3.5 sürümünü hedefleyen [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve System.Core.dll ve kullanarak bir başvuru olduğundan System.Linq yönergesi. Projeden bir veya daha fazla bu gereksinimleri eksikse, bunları el ile ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
