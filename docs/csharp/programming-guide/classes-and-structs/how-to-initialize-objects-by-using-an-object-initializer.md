---
title: Nesne Başlatıcısı kullanarak nesneleri başlatma-C# Programlama Kılavuzu
description: Nesne başlatıcılarının, bir Oluşturucu çağırmadan C# dilinde tür nesnelerini başlatmak için nasıl kullanılacağını öğrenin. Anonim bir tür tanımlamak için bir nesne başlatıcısı kullanın.
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 97f537a8361c612580cc9bb41cef327e310287c2
ms.sourcegitcommit: d66641bc7c14ad7d02300316e9e7e84a875a0a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91712670"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Nesne Başlatıcısı kullanarak nesneleri başlatma (C# Programlama Kılavuzu)

Tür nesnelerini, tür için açıkça bir Oluşturucu çağırmadan, bildirime dayalı olarak başlatmak için nesne başlatıcıları ' nı kullanabilirsiniz.  
  
Aşağıdaki örneklerde, adlandırılmış nesneler ile nesne başlatıcılarının nasıl kullanılacağı gösterilmektedir. Derleyici, önce parametresiz örnek oluşturucusuna erişerek ve sonra üye başlatmaları işleyerek nesne başlatıcıları işler. Bu nedenle, parametresiz Oluşturucu sınıfında olarak bildirilirse `private` , genel erişim gerektiren nesne başlatıcıları başarısız olur.
  
Anonim bir tür tanımlıyorsanız bir nesne Başlatıcısı kullanmanız gerekir. Daha fazla bilgi için bkz. [bir sorgudaki öğe özelliklerinin alt kümelerini döndürme](how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Örnek  

Aşağıdaki örnekte, nesne başlatıcıları kullanarak yeni bir türün nasıl başlatıldığı gösterilmektedir `StudentName` . Bu örnek, türündeki özellikleri ayarlar `StudentName` :
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

Nesne başlatıcıları, bir nesnedeki Dizin oluşturucuyu ayarlamak için kullanılabilir. Aşağıdaki örnek, `BaseballTeam` farklı konumlarda oynatıcı almak ve ayarlamak için bir dizin oluşturucu kullanan bir sınıfı tanımlar. Başlatıcı, konum kısaltmasını veya her bir konum için kullanılan her bir konum için kullanılan sayıyı temel alarak oyuncuları atayabilir:

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Nesne ve Koleksiyon Başlatıcıları](object-and-collection-initializers.md)
