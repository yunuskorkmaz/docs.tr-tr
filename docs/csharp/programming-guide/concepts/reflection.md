---
title: Yansıma (C#)
description: Yansıma, C# içindeki derlemeleri, modülleri ve türleri tanımlayan nesneler sağlar. Kodunuz öznitelikleri içeriyorsa, yansıma bunlara erişmenizi sağlar.
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4d4f4c082dd2d58e212bae53524e5dd4fd06fb75
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302808"
---
# <a name="reflection-c"></a>Yansıma (C#)

Yansıma <xref:System.Type> derlemeleri, modülleri ve türleri tanımlayan nesneler (türü) sağlar. Bir türün örneğini dinamik olarak oluşturmak, türü var olan bir nesneye bağlamak veya var olan bir nesneden türü almak ya da onun yöntemlerini çağırmak ya da alanları ve özelliklerine erişmek için yansıma kullanabilirsiniz. Kodunuzda öznitelikler kullanıyorsanız, yansıma bunlara erişmenizi sağlar. Daha fazla bilgi için bkz. [öznitelikler](../../../standard/attributes/index.md).

<xref:System.Object.GetType> `Object` Bir değişkenin türünü almak için temel sınıftan tüm türler tarafından devralınan yöntemi kullanan basit bir yansıma örneği aşağıda verilmiştir:

> [!NOTE]
> `using System;` `using System.Reflection;` *. Cs* dosyanızın üst kısmına ve eklediğinizden emin olun.

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

Çıktı: `System.Int32` .

Aşağıdaki örnek, yüklü derlemenin tam adını almak için yansıma kullanır.

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

Çıktı: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e` .

> [!NOTE]
> C# anahtar sözcükleri `protected` ve `internal` Il 'de hiçbir anlamı yoktur ve yansıma API 'lerinde kullanılmaz. Il 'deki ilgili terimler *Aile* ve *derlemedir*. `internal`Yansıma kullanarak bir yöntemi tanımlamak için <xref:System.Reflection.MethodBase.IsAssembly%2A> özelliğini kullanın. Bir yöntemi tanımlamak için `protected internal` öğesini kullanın <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A> .

## <a name="reflection-overview"></a>Yansımaya genel bakış

Aşağıdaki durumlarda yansıma yararlı olur:

- Programınızın meta verilerindeki özniteliklere erişmeniz gerektiğinde. Daha fazla bilgi için bkz. [özniteliklerde depolanan bilgileri alma](../../../standard/attributes/retrieving-information-stored-in-attributes.md).
- Bir derlemedeki türleri İnceleme ve örnekleme için.
- Çalışma zamanında yeni türler oluşturmak için. İçinde sınıfları kullanın <xref:System.Reflection.Emit> .
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
