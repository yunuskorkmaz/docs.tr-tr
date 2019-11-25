---
title: Nesne Başlatıcısı kullanarak nesneleri başlatma- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: be555688a645c7689e76b5b4499c44255c18dbc8
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970873"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Nesne Başlatıcısı kullanarak nesneleri başlatma (C# Programlama Kılavuzu)

Tür nesnelerini, tür için açıkça bir Oluşturucu çağırmadan, bildirime dayalı olarak başlatmak için nesne başlatıcıları ' nı kullanabilirsiniz.  
  
Aşağıdaki örneklerde, adlandırılmış nesneler ile nesne başlatıcılarının nasıl kullanılacağı gösterilmektedir. Derleyici, önce varsayılan örnek oluşturucusuna erişerek ve sonra üye başlatmaları işleyerek nesne başlatıcıları işler. Bu nedenle, parametresiz Oluşturucu sınıfında `private` olarak bildirilirse, genel erişim gerektiren nesne başlatıcıları başarısız olur.
  
Anonim bir tür tanımlıyorsanız bir nesne Başlatıcısı kullanmanız gerekir. Daha fazla bilgi için bkz. [bir sorgudaki öğe özelliklerinin alt kümelerini döndürme](how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Örnek  

Aşağıdaki örnekte, nesne başlatıcıları kullanarak yeni bir `StudentName` türünün nasıl başlatılacağını gösterilmektedir. Bu örnek `StudentName` türündeki özellikleri ayarlar:
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

Nesne başlatıcıları, bir nesnedeki Dizin oluşturucuyu ayarlamak için kullanılabilir. Aşağıdaki örnek, farklı konumlarda oynatıcı almak ve ayarlamak için bir dizin oluşturucu kullanan bir `BaseballTeam` sınıfını tanımlar. Başlatıcı, konum kısaltmasını veya her bir konum için kullanılan her bir konum için kullanılan sayıyı temel alarak oyuncuları atayabilir:

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Nesne ve Koleksiyon Başlatıcıları](object-and-collection-initializers.md)
