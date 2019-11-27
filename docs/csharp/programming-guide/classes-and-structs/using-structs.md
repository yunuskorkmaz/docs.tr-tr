---
title: Yapıları kullanma- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 491ee0224ffa39262992f7f42d20e5f97560b73f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429497"
---
# <a name="using-structs-c-programming-guide"></a>Yapıları kullanma (C# Programlama Kılavuzu)

`struct` türü `Point`, `Rectangle`ve `Color`gibi hafif nesneleri temsil etmek için uygundur. Bir noktayı [Otomatik uygulanmış özelliklerle](./auto-implemented-properties.md)bir [sınıf](../../language-reference/keywords/class.md) olarak temsil etmek uygun olsa da, bazı senaryolarda bir [Yapı](../../language-reference/keywords/struct.md) daha verimli olabilir. Örneğin, 1000 `Point` nesnelerden oluşan bir dizi bildirirseniz, her bir nesneye başvurmak için ek bellek ayırabilirsiniz; Bu durumda, bir yapı daha pahalı olur. .NET zaten <xref:System.Drawing.Point>adlı bir nesne içerdiğinden, bu örnekteki yapı bunun yerine `Coords` olarak adlandırılmıştır.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

Bir struct için parametresiz bir Oluşturucu tanımlamak hatadır. Bir yapı gövdesinde örnek alanı başlatmak da bir hatadır. Yalnızca parametreli bir oluşturucuyu, örtük, parametresiz oluşturucuyu, [nesne başlatıcısını](object-and-collection-initializers.md)kullanarak veya yapı oluşturulduktan sonra üyelere ayrı ayrı erişerek, dışarıdan erişilebilen yapı üyelerini başlatabilirsiniz. Herhangi bir özel veya başka şekilde erişilemeyen üye, oluşturucuların yalnızca kullanımını gerektirir.

[New](../../language-reference/operators/new-operator.md) işlecini kullanarak bir struct nesnesi oluşturduğunuzda, oluşturulur ve uygun Oluşturucu [oluşturucunun imzasına](constructors.md#constructor-syntax)göre çağırılır. Sınıfların aksine, yapılar `new` işleci kullanılmadan örneklenebilir. Böyle bir durumda, bir Oluşturucu çağrısı yoktur ve bu da ayırmayı daha verimli hale getirir. Ancak alanlar atanmamış olarak kalır ve tüm alanlar başlatılana kadar nesne kullanılamaz. Bu, özellikler aracılığıyla değerleri almak veya ayarlamak için bir değer içerir.

Parametresiz oluşturucuyu kullanarak bir yapı nesnesi örneği oluşturursanız, tüm Üyeler [varsayılan değerlerine](../../language-reference/keywords/default-values-table.md)göre atanır.

Bir yapı için parametrelere sahip bir Oluşturucu yazarken, tüm üyeleri açık olarak başlatmalısınız; Aksi takdirde bir veya daha fazla üye atanmamış olarak kalır ve yapı birimi [CS0171](../../misc/cs0171.md), derleyici hatası üretirken kullanılamaz.

Sınıflar için olduğu gibi yapılar için devralma yoktur. Yapı, başka bir struct veya sınıftan devralınabilir ve bir sınıfın temeli olamaz. Ancak yapılar, temel sınıftan devralınır <xref:System.Object>. Bir struct, arabirimler uygulayabilir ve tam olarak sınıfların yaptığı şekilde yapılır.

Anahtar sözcüğünü kullanarak bir sınıf bildiremezsiniz `struct`. İçinde C#, sınıflar ve yapılar anlamsal olarak farklıdır. Yapı bir değer türüdür, ancak bir sınıf bir başvuru türüdür. Daha fazla bilgi için bkz. [değer türleri](../../language-reference/keywords/value-types.md) ve [başvuru türleri](../../language-reference/keywords/reference-types.md).

Başvuru türü semantiklerine ihtiyacınız yoksa, bunun yerine bir yapı olarak bildirirseniz küçük bir sınıf sistem tarafından daha verimli bir şekilde işlenebilir.

## <a name="example-1"></a>Örnek 1

Bu örnekte, hem parametresiz hem de parametreli oluşturucular kullanılarak `struct` başlatma gösterilmektedir.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]

## <a name="example-2"></a>Örnek 2

Bu örnek, yapılar için benzersiz olan bir özelliği gösterir. `new` işlecini kullanmadan bir CoOrds nesnesi oluşturur. Word `struct` sözcüğünü `class`Word ile değiştirirseniz, program derlenmez.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](index.md)
- [Yapılar](structs.md)
