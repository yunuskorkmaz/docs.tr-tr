---
title: 'Nasıl yapılır: Koleksiyon Başlatıcısı ile bir Sözlük Başlatma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: b8c44ebbdc89d72398c3380d708b45d0b7dfdad3
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39198464"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Nasıl yapılır: Koleksiyon Başlatıcısı ile bir Sözlük Başlatma (C# Programlama Kılavuzu)
A <xref:System.Collections.Generic.Dictionary`2> anahtar/değer çiftleri koleksiyonu içerir. Kendi <xref:System.Collections.Generic.Dictionary`2.Add*> yöntemi biri anahtar ve değer için bir tane olmak üzere iki parametre alır. Başlatmak için bir <xref:System.Collections.Generic.Dictionary`2>, ya da herhangi bir koleksiyon olan `Add` yöntemi birden çok parametre alır, aşağıdaki örnekte gösterildiği gibi her parametre kümesi ayraçlarının içine alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, bir <xref:System.Collections.Generic.Dictionary`2> türünün bir örneğini ile başlatılmış `StudentName`.  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 Küme ayraçları içine koleksiyonun her öğesine iki çiftleri unutmayın. Nesne Başlatıcısı için en içteki ayraç içine `StudentName`, ve en dıştaki ayraç içine eklenecek anahtar/değer çifti için Başlatıcı `students` <xref:System.Collections.Generic.Dictionary`2>. Son olarak, tüm koleksiyon Başlatıcısı sözlüğü için parantez içine alınır.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu çalıştırmak için kopyalayın ve Visual Studio'da oluşturulan bir Visual C# konsol uygulaması projesi sınıfı yapıştırın. Varsayılan olarak, bu proje 3.5 sürümünü hedefleyen [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve System.Core.dll ve kullanarak bir başvuru olduğundan System.Linq yönergesi. Projeden bir veya daha fazla bu gereksinimleri eksikse, bunları el ile ekleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
