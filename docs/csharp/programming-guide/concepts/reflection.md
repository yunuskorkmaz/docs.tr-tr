---
title: Yansıma (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711668"
---
# <a name="reflection-c"></a>Yansıma (C#)

Yansıma, derlemeleri, <xref:System.Type>modülleri ve türleri açıklayan nesneler (tür) sağlar. Yansımayı dinamik olarak bir tür örneği oluşturmak, türü varolan bir nesneye bağlamak veya türü varolan bir nesneden almak ve yöntemlerini çağırmak veya alanlarına ve özelliklerine erişmek için kullanabilirsiniz. Kodunuzda öznitelikler kullanıyorsanız, yansıma bunlara erişmenizi sağlar. Daha fazla bilgi için [Özniteliklere](../../../standard/attributes/index.md)bakın.

Bir değişken türünü elde etmek <xref:System.Object.GetType> için `Object` temel sınıftan tüm türler tarafından devralınan yöntemi kullanarak yansımabasit bir örnek aşağıda verilmiştir:

> [!NOTE]
> *.cs* `using System;` dosyanızın üst kısmında ve `using System.Reflection;` eklentisini yaptığınızdan emin olun.

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

Çıktı: `System.Int32`.

Aşağıdaki örnek, yüklenen derlemenin tam adını elde etmek için yansımayı kullanır.

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

Çıktı: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.

> [!NOTE]
> C# anahtar `protected` `internal` kelimeleri il'de bir anlam ifade etmez ve yansıma API'lerinde kullanılmaz. IL'de karşılık gelen terimler *Aile* ve *Meclis'tir.* Yansımayı `internal` kullanarak bir yöntem <xref:System.Reflection.MethodBase.IsAssembly%2A> tanımlamak için özelliği kullanın. Bir `protected internal` yöntemi tanımlamak için, <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.

## <a name="reflection-overview"></a>Yansımaya genel bakış

Yansıma aşağıdaki durumlarda yararlıdır:

- Programınızın meta verilerindeki özniteliklere erişmeniz gerektiğinde. Daha fazla bilgi için [bkz.](../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- Montajdaki türleri incelemek ve anlık olarak incelemek için.
- Çalışma zamanında yeni türler oluşturmak için. Sınıfları <xref:System.Reflection.Emit>' da kullan.
- Geç bağlama gerçekleştirmek için, çalışma zamanında oluşturulan türlerdeki yöntemlere erişin. Konuya Dinamik [Yükleme ve Kullanma Türleri'ni](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)görün.

## <a name="related-sections"></a>İlgili bölümler

Daha fazla bilgi için:

- [Yansıma](../../../framework/reflection-and-codedom/reflection.md)
- [Tür Bilgilerini Görüntüleme](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [Yansıma ve Genel Türler](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [Özniteliklerde Depolanan Bilgileri Alma](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
