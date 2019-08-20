---
title: Erişimci erişilebilirliği kısıtlama- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: ca990693d29f8c8abd2e4ba2488a429a797afaec
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596179"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Erişimci Erişilebilirliğini Kısıtlama (C# Programlama Kılavuzu)
Bir özelliğin veya dizin oluşturucunun [Get](../../language-reference/keywords/get.md) ve [set](../../language-reference/keywords/set.md) bölümlerine *erişimciler*denir. Varsayılan olarak, bu erişimciler ait oldukları özelliğin veya dizin oluşturucunun aynı görünürlük veya erişim düzeyine sahiptir. Daha fazla bilgi için bkz. [Erişilebilirlik düzeyleri](../../language-reference/keywords/accessibility-levels.md). Ancak, bu Erişimcilerde erişimi kısıtlamak bazen yararlı olur. Genellikle bu, erişimcinin erişilebilirliğini `set` kısıtlamadan, `get` erişimcinin genel olarak erişilebilir tutulması ile ilgilidir. Örneğin:  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 Bu örnekte, adlı `Name` bir özellik bir `get` ve `set` erişimcisi tanımlar. Erişimci, özelliğin `public` kendi erişilebilirlik düzeyini alır, `set` bu durumda erişimci kendisine korumalı erişim değiştiricisi uygulanarak açıkça kısıtlanır. [](../../language-reference/keywords/protected.md) `get`  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Erişimcilerde erişim değiştiricilerine yönelik kısıtlamalar  
 Özelliklerde veya dizin oluşturucularda erişimci değiştiricilerin kullanılması şu koşullara tabidir:  
  
- Bir arabirimde veya açık [arabirim](../../language-reference/keywords/interface.md) üyesi uygulamasında erişimci değiştiricileri kullanamazsınız.  
  
- Erişimci değiştiricileri yalnızca özellik veya dizin oluşturucunun hem hem `set` `get` de erişimcileri varsa kullanabilirsiniz. Bu durumda, değiştiriciye yalnızca iki erişimcinin yalnızca birinde izin verilir.  
  
- Özelliğin veya dizin oluşturucunun bir [geçersiz kılma](../../language-reference/keywords/override.md) değiştiricisi varsa, erişimci değiştiricisi, varsa geçersiz kılınan erişimcinin erişimcisi ile eşleşmelidir.  
  
- Erişimcinin erişilebilirlik düzeyi, özelliğin veya dizin oluşturucunun kendi erişilebilirlik düzeyinden daha kısıtlayıcı olmalıdır.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Geçersiz kılma erişimcileri üzerindeki erişim değiştiricileri  
 Bir özelliği veya dizin oluşturucuyu geçersiz kıldığınızda geçersiz kılınan erişimcilere geçersiz kılma kodu tarafından erişilebilir olması gerekir. Ayrıca, hem Property/Indexer hem de erişimcilerinin erişilebilirliği karşılık gelen geçersiz kılınan Özellik/Dizin Oluşturucu ve erişimcileri ile eşleşmelidir. Örneğin:  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a>Arabirimleri uygulama  
 Bir arabirim uygulamak için erişimci kullandığınızda, erişimci bir erişim değiştiricisine sahip olmayabilir. Ancak, gibi bir erişimci `get`kullanarak arabirimi uygularsanız, diğer erişimci aşağıdaki örnekte olduğu gibi bir erişim değiştiricisine sahip olabilir:  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a>Erişimci erişilebilirlik etki alanı  
 Erişimci üzerinde bir erişim değiştiricisi kullanırsanız, erişimcinin [erişilebilirlik etki alanı](../../language-reference/keywords/accessibility-domain.md) bu değiştiriciye göre belirlenir.  
  
 Erişimci üzerinde bir erişim değiştiricisi kullanmıyorsanız, erişimcinin erişilebilirlik etki alanı, özelliğin veya dizin oluşturucunun erişilebilirlik düzeyine göre belirlenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek üç sınıf `BaseClass` `DerivedClass`içerir,, ve `MainClass`. Üzerinde `BaseClass` `Name` ve herikisınıftaikiözelliğivardır.`Id` Örnek, [korumalı](../../language-reference/keywords/protected.md) veya [özel](../../language-reference/keywords/private.md)gibi kısıtlayıcı `DerivedClass` bir erişim değiştiricisi kullandığınızda üzerinde özelliğinin `Id` `Id` nasıl `BaseClass` gizlendiğini gösterir. Bu nedenle, bu özelliğe değer atadığınızda, `BaseClass` sınıfındaki özelliği yerine çağırılır. Erişim değiştiricisinin [genel](../../language-reference/keywords/public.md) olarak değiştirilmesi, özelliği erişilebilir hale getirir.  
  
 Örnek ayrıca `private` , içindeki `Name` `protected` özelliğininerişimcisinde`set` bulunan veya gibi kısıtlayıcı bir erişim değiştiricisinin erişimciye erişimi önlediği ve ' a atarken bir hata üretmesinin gerektiğini gösterir. `DerivedClass` içerdiği.  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a>Açıklamalar  
 Bildirimini `new private string Id` ile`new public string Id`değiştirmeniz durumunda çıktıyı alırsınız:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özellikler](./properties.md)
- [Dizin Oluşturucular](../indexers/index.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
