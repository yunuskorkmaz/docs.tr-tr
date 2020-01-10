---
title: Erişimci erişilebilirliği kısıtlama- C# Programlama Kılavuzu
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714689"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Erişimci Erişilebilirliğini Kısıtlama (C# Programlama Kılavuzu)
Bir özelliğin veya dizin oluşturucunun [Get](../../language-reference/keywords/get.md) ve [set](../../language-reference/keywords/set.md) bölümlerine *erişimciler*denir. Varsayılan olarak, bu erişimciler ait oldukları özelliğin veya dizin oluşturucunun aynı görünürlük veya erişim düzeyine sahiptir. Daha fazla bilgi için bkz. [Erişilebilirlik düzeyleri](../../language-reference/keywords/accessibility-levels.md). Ancak, bu Erişimcilerde erişimi kısıtlamak bazen yararlı olur. Genellikle, bu, `get` erişimcinin genel olarak erişilebilir tutulması sırasında `set` erişimcisinin erişilebilirliğini kısıtlamayı içerir. Örneğin:  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 Bu örnekte, `Name` adlı bir özellik `get` ve `set` erişimcisini tanımlar. `get` erişimcisi özelliğin erişilebilirlik düzeyini alır, bu durumda `public` `set` erişimci, erişimci kendisine [korumalı](../../language-reference/keywords/protected.md) erişim değiştiricisi uygulanarak açıkça kısıtlanır.  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Erişimcilerde erişim değiştiricilerine yönelik kısıtlamalar  
 Özelliklerde veya dizin oluşturucularda erişimci değiştiricilerin kullanılması şu koşullara tabidir:  
  
- Bir arabirimde veya açık [arabirim](../../language-reference/keywords/interface.md) üyesi uygulamasında erişimci değiştiricileri kullanamazsınız.  
  
- Erişimci değiştiricilerini yalnızca özellik veya dizin oluşturucunun hem `set` hem de `get` erişimcileri varsa kullanabilirsiniz. Bu durumda, değiştiriciye yalnızca iki erişimcinin yalnızca birinde izin verilir.  
  
- Özelliğin veya dizin oluşturucunun bir [geçersiz kılma](../../language-reference/keywords/override.md) değiştiricisi varsa, erişimci değiştiricisi, varsa geçersiz kılınan erişimcinin erişimcisi ile eşleşmelidir.  
  
- Erişimcinin erişilebilirlik düzeyi, özelliğin veya dizin oluşturucunun kendi erişilebilirlik düzeyinden daha kısıtlayıcı olmalıdır.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Geçersiz kılma erişimcileri üzerindeki erişim değiştiricileri  
 Bir özelliği veya dizin oluşturucuyu geçersiz kıldığınızda geçersiz kılınan erişimcilere geçersiz kılma kodu tarafından erişilebilir olması gerekir. Ayrıca, hem Property/Indexer hem de erişimcilerinin erişilebilirliği karşılık gelen geçersiz kılınan Özellik/Dizin Oluşturucu ve erişimcileri ile eşleşmelidir. Örneğin:  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a>Arabirimleri uygulama  
 Bir arabirim uygulamak için erişimci kullandığınızda, erişimci bir erişim değiştiricisine sahip olmayabilir. Ancak, `get`gibi bir erişimci kullanarak arabirimi uygularsanız, diğer erişimci aşağıdaki örnekte olduğu gibi bir erişim değiştiricisine sahip olabilir:  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a>Erişimci erişilebilirlik etki alanı  
 Erişimci üzerinde bir erişim değiştiricisi kullanırsanız, erişimcinin [erişilebilirlik etki alanı](../../language-reference/keywords/accessibility-domain.md) bu değiştiriciye göre belirlenir.  
  
 Erişimci üzerinde bir erişim değiştiricisi kullanmıyorsanız, erişimcinin erişilebilirlik etki alanı, özelliğin veya dizin oluşturucunun erişilebilirlik düzeyine göre belirlenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `BaseClass`, `DerivedClass`ve `MainClass`üç sınıf içerir. `BaseClass`, `Name` ve `Id` her iki sınıfta da iki özellik vardır. Örnek, [korumalı](../../language-reference/keywords/protected.md) veya [özel](../../language-reference/keywords/private.md)gibi kısıtlayıcı bir erişim değiştiricisi kullandığınızda, `DerivedClass` üzerindeki özelliğin `Id` Özellik `BaseClass` `Id` nasıl gizlenemeyeceğini gösterir. Bu nedenle, bu özelliğe değer atadığınızda, bunun yerine `BaseClass` sınıfındaki özellik çağrılır. Erişim değiştiricisinin [genel](../../language-reference/keywords/public.md) olarak değiştirilmesi, özelliği erişilebilir hale getirir.  
  
 Örnek ayrıca, `private` veya `protected`gibi kısıtlayıcı bir erişim değiştiricisinin, `DerivedClass` 'teki `Name` özelliğinin `set` erişimcisinde, erişimciye erişimi önlediği ve kendisine atarken bir hata oluşturduğu bir hata üreten bir hata üretir.  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a>Açıklamalar  
 Bildirim `new private string Id` `new public string Id`ile değiştirirseniz, çıktıyı alırsınız:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Veri Erişimi](./properties.md)
- [Dizin Oluşturucular](../indexers/index.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
