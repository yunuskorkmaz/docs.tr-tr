---
title: Yansıma (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711668"
---
# <a name="reflection-c"></a>Yansıma (C#)

Yansıma derlemeleri, modülleri ve türleri tanımlayan nesneler (<xref:System.Type>türünde) sağlar. Bir türün örneğini dinamik olarak oluşturmak, türü var olan bir nesneye bağlamak veya var olan bir nesneden türü almak ya da onun yöntemlerini çağırmak ya da alanları ve özelliklerine erişmek için yansıma kullanabilirsiniz. Kodunuzda öznitelikler kullanıyorsanız, yansıma bunlara erişmenizi sağlar. Daha fazla bilgi için bkz. [öznitelikler](../../../standard/attributes/index.md).

Bir değişkenin türünü almak için `Object` temel sınıfından tüm türler tarafından devralınan <xref:System.Object.GetType> yöntemi kullanılarak oluşan basit bir yansıma örneğidir:

> [!NOTE]
> *. Cs* dosyanızın üst kısmına `using System;` ve `using System.Reflection;` eklediğinizden emin olun.

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

Çıktı: `System.Int32`.

Aşağıdaki örnek, yüklü derlemenin tam adını almak için yansıma kullanır.

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

Çıktı: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.

> [!NOTE]
> `protected` C# ve `internal` anahtar kelimelerinde hiçbir anlamı yoktur ve yansıma API 'lerinde kullanılmaz. Il 'deki ilgili terimler *Aile* ve *derlemedir*. Yansıma kullanarak bir `internal` yöntemi tanımlamak için <xref:System.Reflection.MethodBase.IsAssembly%2A> özelliğini kullanın. `protected internal` yöntemi tanımlamak için <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>kullanın.

## <a name="reflection-overview"></a>Yansımaya genel bakış

Aşağıdaki durumlarda yansıma yararlı olur:

- Programınızın meta verilerindeki özniteliklere erişmeniz gerektiğinde. Daha fazla bilgi için bkz. [özniteliklerde depolanan bilgileri alma](../../../standard/attributes/retrieving-information-stored-in-attributes.md).
- Bir derlemedeki türleri İnceleme ve örnekleme için.
- Çalışma zamanında yeni türler oluşturmak için. <xref:System.Reflection.Emit>sınıfları kullanın.
- Geç bağlama gerçekleştirmek için çalışma zamanında oluşturulan türler üzerindeki yöntemlere erişme. [Türleri dinamik olarak yükleme ve kullanma](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)konusuna bakın.

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
