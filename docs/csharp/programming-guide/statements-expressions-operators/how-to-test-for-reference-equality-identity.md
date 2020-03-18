---
title: Referans eşitliği (Identity) için nasıl test yapılır ?
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 77ce2ef0ccf47d619134c120101ba2aa04f485e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75699060"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Referans eşitliği (Identity) (C# Programlama Kılavuzu) için nasıl test yapılır?
Türlerinizde başvuru eşitliği karşılaştırmalarını desteklemek için herhangi bir özel mantık uygulamanız gerekmez. Bu işlevsellik statik <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> yöntem ile tüm türler için sağlanır.  
  
 Aşağıdaki örnek, iki değişkenin referans *eşitliği*olup olmadığını nasıl belirleyeceklerini gösterir , bu da bellekte aynı nesneye atıfta bulunduğu anlamına gelir.  
  
 Örnek, neden <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> her `false` zaman değer türleri için döndürür ve dize eşitliğini belirlemek için neden kullanmamanız <xref:System.Object.ReferenceEquals%2A> gerektiğini de gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 Evrensel taban `Equals` sınıfında uygulanması da bir başvuru eşitliği denetimi gerçekleştirir, ancak bir sınıf yöntemi geçersiz kılmak için olur, çünkü bu kullanmak için en iyisidir, sonuçlar beklediğiniz olmayabilir. <xref:System.Object?displayProperty=nameWithType> Aynı ve `==` `!=` operatörler için de geçerlidir. Başvuru türlerinde çalışırken, varsayılan davranış `==` ve `!=` bir başvuru eşitliği denetimi gerçekleştirmektir. Ancak, türetilen sınıflar bir değer eşitliği denetimi gerçekleştirmek için işleci aşırı yükleyebilir. Hata potansiyelini en aza indirmek için, <xref:System.Object.ReferenceEquals%2A> iki nesnenin başvuru eşitliğiolup olmadığını belirlemeniz gerektiğinde her zaman kullanmak en iyisidir.  
  
 Aynı derleme içindeki sabit dizeleri her zaman çalışma süresine göre interned. Diğer bir tanesi, her benzersiz edebi dizenin yalnızca bir örneği korunur. Ancak, çalışma zamanı, çalışma zamanında oluşturulan dizeleri interned garanti etmez, ne de farklı derlemelerde iki eşit sabit dizeleri interned garanti etmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eşitlik Karşılaştırmaları](./equality-comparisons.md)
