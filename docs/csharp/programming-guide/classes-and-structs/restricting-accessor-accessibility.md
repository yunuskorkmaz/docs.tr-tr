---
title: Erişimci erişilebilirliği kısıtlama-C# Programlama Kılavuzu
description: C# içindeki bir özelliğin get ve set erişimcileri, varsayılan olarak ait oldukları özellik olarak aynı görünürlük veya erişim düzeyine sahiptir. Erişimi kısıtlayabilirsiniz.
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: be7be4fc67a9a6f62a71f8473d6daa1fac49e842
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199035"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Erişimci Erişilebilirliğini Kısıtlama (C# Programlama Kılavuzu)

Bir özelliğin veya dizin oluşturucunun [Get](../../language-reference/keywords/get.md) ve [set](../../language-reference/keywords/set.md) bölümlerine *erişimciler*denir. Varsayılan olarak, bu erişimciler ait oldukları özelliğin veya dizin oluşturucunun aynı görünürlük veya erişim düzeyine sahiptir. Daha fazla bilgi için bkz. [Erişilebilirlik düzeyleri](../../language-reference/keywords/accessibility-levels.md). Ancak, bu Erişimcilerde erişimi kısıtlamak bazen yararlı olur. Genellikle bu, erişimcinin erişilebilirliğini kısıtlamadan `set` , `get` erişimcinin genel olarak erişilebilir tutulması ile ilgilidir. Örneğin:  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 Bu örnekte, adlı bir özellik `Name` bir `get` ve erişimcisi tanımlar `set` . Erişimci, `get` özelliğin kendi erişilebilirlik düzeyini alır, `public` Bu durumda `set` erişimci kendisine [korumalı](../../language-reference/keywords/protected.md) erişim değiştiricisi uygulanarak açıkça kısıtlanır.  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Erişimcilerde erişim değiştiricilerine yönelik kısıtlamalar  

 Özelliklerde veya dizin oluşturucularda erişimci değiştiricilerin kullanılması şu koşullara tabidir:  
  
- Bir arabirimde veya açık [arabirim](../../language-reference/keywords/interface.md) üyesi uygulamasında erişimci değiştiricileri kullanamazsınız.  
  
- Erişimci değiştiricileri yalnızca özellik veya dizin oluşturucunun hem hem de erişimcileri varsa kullanabilirsiniz `set` `get` . Bu durumda, değiştiriciye yalnızca iki erişimcinin yalnızca birinde izin verilir.  
  
- Özelliğin veya dizin oluşturucunun bir [geçersiz kılma](../../language-reference/keywords/override.md) değiştiricisi varsa, erişimci değiştiricisi, varsa geçersiz kılınan erişimcinin erişimcisi ile eşleşmelidir.  
  
- Erişimcinin erişilebilirlik düzeyi, özelliğin veya dizin oluşturucunun kendi erişilebilirlik düzeyinden daha kısıtlayıcı olmalıdır.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Geçersiz kılma erişimcileri üzerindeki erişim değiştiricileri  

 Bir özelliği veya dizin oluşturucuyu geçersiz kıldığınızda geçersiz kılınan erişimcilere geçersiz kılma kodu tarafından erişilebilir olması gerekir. Ayrıca, hem Property/Indexer hem de erişimcilerinin erişilebilirliği karşılık gelen geçersiz kılınan Özellik/Dizin Oluşturucu ve erişimcileri ile eşleşmelidir. Örneğin:  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a>Arabirimleri uygulama  

 Bir arabirim uygulamak için erişimci kullandığınızda, erişimci bir erişim değiştiricisine sahip olmayabilir. Ancak, gibi bir erişimci kullanarak arabirimi uygularsanız, `get` diğer erişimci aşağıdaki örnekte olduğu gibi bir erişim değiştiricisine sahip olabilir:  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a>Erişimci erişilebilirlik etki alanı  

 Erişimci üzerinde bir erişim değiştiricisi kullanırsanız, erişimcinin [erişilebilirlik etki alanı](../../language-reference/keywords/accessibility-domain.md) bu değiştiriciye göre belirlenir.  
  
 Erişimci üzerinde bir erişim değiştiricisi kullanmıyorsanız, erişimcinin erişilebilirlik etki alanı, özelliğin veya dizin oluşturucunun erişilebilirlik düzeyine göre belirlenir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek üç sınıf içerir,, `BaseClass` `DerivedClass` ve `MainClass` . Üzerinde `BaseClass` `Name` ve `Id` her iki sınıfta iki özelliği vardır. Örnek, `Id` `DerivedClass` `Id` `BaseClass` [korumalı](../../language-reference/keywords/protected.md) veya [özel](../../language-reference/keywords/private.md)gibi kısıtlayıcı bir erişim değiştiricisi kullandığınızda üzerinde özelliğinin nasıl gizlendiğini gösterir. Bu nedenle, bu özelliğe değer atadığınızda, `BaseClass` sınıfındaki özelliği yerine çağırılır. Erişim değiştiricisinin [genel](../../language-reference/keywords/public.md) olarak değiştirilmesi, özelliği erişilebilir hale getirir.  
  
 Örnek ayrıca, `private` içindeki özelliğinin erişimcisinde bulunan veya gibi kısıtlayıcı bir erişim `protected` `set` `Name` `DerivedClass` değiştiricisinin erişimciye erişimi önlediği ve kendisine atarken bir hata oluşturduğu bir hata üretdiğini gösterir.  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a>Yorumlar  

 Bildirimini ile değiştirmeniz durumunda `new private string Id` `new public string Id` çıktıyı alırsınız:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özellikler](./properties.md)
- [Dizin Oluşturucular](../indexers/index.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
