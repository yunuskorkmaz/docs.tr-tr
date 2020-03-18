---
title: Erişime Erişimin Kısıtlanması - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: a332fef814f0c81914eb7b8c308de68f719fbaac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714689"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Erişimci Erişilebilirliğini Kısıtlama (C# Programlama Kılavuzu)
Bir özelliğin veya dizinleyicinin [alın](../../language-reference/keywords/get.md) ve [ayarla](../../language-reference/keywords/set.md) *bölümlerine erişimci*denir. Varsayılan olarak bu erişimedenler, ait oldukları özellik veya dizinleyicinin aynı görünürlüğüne veya erişim düzeyine sahiptir. Daha fazla bilgi için [erişilebilirlik düzeylerine](../../language-reference/keywords/accessibility-levels.md)bakın. Ancak, bazen bu erişime erişimin kısıtlanması yararlıdır. Genellikle, bu, `set` erişime erişimin kısıtlanmasıve erişimin `get` herkese açık tutulmasını içerir. Örnek:  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 Bu örnekte, adlı `Name` bir `get` özellik `set` a ve erişimci tanımlar. Bu `get` durumda, erişimci, [korumalı](../../language-reference/keywords/protected.md) erişim `public` değiştiriciyi erişimsahibinin kendisine uygulanarak açıkça kısıtlanırken, `set` erişimsahibi özelliğin erişilebilirlik düzeyini alır.  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Erişimcilere Erişim Kısıtlamaları  
 Özellik veya dizinleyiciler üzerinde aksesuar değiştiricilerin kullanılması aşağıdaki koşullara tabidir:  
  
- Bir arabirimde veya açık [arabirim](../../language-reference/keywords/interface.md) üyesi uygulamasında erişim değiştirici leri kullanamazsınız.  
  
- Erişim değiştiricileri yalnızca özellik veya dizinleyicihem `set` de `get` erişimciler varsa kullanabilirsiniz. Bu durumda, değiştirici yalnızca iki erişimcilerin birinde izin verilir.  
  
- Özellik veya dizinleyicibir [geçersiz kılma](../../language-reference/keywords/override.md) değiştirici varsa, erişimdeğiştirici geçersiz kılınan erişime sahip, varsa, geçersiz kılınan erişime sahip olanla eşleşmelidir.  
  
- Erişilebilirlik düzeyi, özellik veya dizinleyicinin kendisindeki erişilebilirlik düzeyinden daha kısıtlayıcı olmalıdır.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Access'i Geçersiz Kılanlar'da Değiştiricilere Erişin  
 Bir özelliği veya dizinleyiciyi geçersiz kaldığınızda, geçersiz kılınan erişime erişilenler için geçersiz kılınan koda erişilebilmelidir. Ayrıca, hem özellik/dizinleyicinin hem de erişime girenlerin ilgili geçersiz kılınan özellik/dizinleyici ile ve erişime girenlerle eşleşmesi gerekir. Örnek:  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a>Arayüzleri Uygulama  
 Arabirimi uygulamak için bir erişimci kullandığınızda, erişimsahibinin bir erişim değiştiricisi olmayabilir. Ancak, arabirimi aşağıdaki örnekte olduğu gibi, diğer erişimcinin bir erişim değiştiricisi olabilir gibi `get`bir erişimci kullanarak uygularsanız:  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a>Erişilebilirlik Etki Alanı  
 Erişim değiştiriciüzerinde bir erişim değiştiricisi kullanıyorsanız, erişime [erişim etki alanı](../../language-reference/keywords/accessibility-domain.md) bu değiştirici tarafından belirlenir.  
  
 Erişim değiştiriciüzerinde bir erişim değiştirici kullanmadıysanız, erişime erişim etki alanı özellik veya dizinleyicinin erişilebilirlik düzeyine göre belirlenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte üç `BaseClass`sınıf `DerivedClass`ve `MainClass`. `BaseClass` `Name` Ve `Id` her iki sınıfta iki özellik vardır. Örnek, [korumalı](../../language-reference/keywords/protected.md) [veya](../../language-reference/keywords/private.md)özel gibi kısıtlayıcı `Id` `BaseClass` bir erişim değiştirici kullandığınızda üzerindeki `Id` `DerivedClass` özelliğin özellik tarafından nasıl gizlenebileceğini gösterir. Bu nedenle, bu özelliğe değer atadığınızda, `BaseClass` sınıfüzerindeki özellik bunun yerine çağrılır. Erişim değiştiricinin [genel](../../language-reference/keywords/public.md) tarafından değiştirilmesi özelliği erişilebilir hale getirecektir.  
  
 Örnek ayrıca, `private` `protected` `set` `Name` özellik erişimcisi gibi kısıtlayıcı bir erişim değiştiricinin erişime erişimi `DerivedClass` engellediğini ve ona atadığınızda bir hata oluşturduğunu da gösterir.  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a>Yorumlar  
 Bildirimi `new private string Id` değiştirirseniz `new public string Id`çıktıyı alırsınız:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özellikler](./properties.md)
- [Dizin Oluşturucular](../indexers/index.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
