---
title: Nesne başharflerini kullanarak nesneleri başlatma - C# Programlama Kılavuzu
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: a2ecc9df211d0082bd4b413653e374758c877abc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705593"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Nesne başharfi (C# Programlama Kılavuzu) kullanarak nesneleri başlatma

Tür için açıkça bir oluşturucu çağırmadan, tür nesnelerini açıklayıcı bir şekilde başlatmak için nesne başharflerini kullanabilirsiniz.  
  
Aşağıdaki örnekler, adlandırılmış nesnelerle nesne baş harflerinin nasıl kullanılacağını gösterir. Derleyici, önce varsayılan örnek oluşturucuya erişerek ve daha sonra üye başlatmaişlemlerini işleyerek nesne başlatılmasını işler. Bu nedenle, parametresiz oluşturucu `private` sınıfta olduğu gibi bildirilirse, ortak erişim gerektiren nesne baş harfleri başarısız olur.
  
Anonim bir tür tanımlıyorsanız, nesne baş harflerini kullanmanız gerekir. Daha fazla bilgi için, [sorgudaki öğe özelliklerialt kümelerini nasıl döndürürsünüz](how-to-return-subsets-of-element-properties-in-a-query.md)bkz.  
  
## <a name="example"></a>Örnek  

Aşağıdaki örnek, nesne başharflerini `StudentName` kullanarak yeni bir türün nasıl baş harfe çarptırılabildiğini gösterir. Bu örnek, `StudentName` türözellikleri ayarlar:
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

Nesne baş harfleri bir nesnedeki dizinleyicileri ayarlamak için kullanılabilir. Aşağıdaki örnek, oyuncuları `BaseballTeam` farklı konumlara almak ve ayarlamak için dizinleyici kullanan bir sınıf tanımlar. Baş harf, pozisyonun kısaltması veya her pozisyon beyzbol karneleri için kullanılan sayıya bağlı olarak oyuncu atayabilir:

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Nesne ve Koleksiyon Başlatıcıları](object-and-collection-initializers.md)
