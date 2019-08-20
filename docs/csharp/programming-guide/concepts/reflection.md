---
title: Yansıma (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 0828e59f74ac0c7575df2cea531caa0d42a2dd96
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590764"
---
# <a name="reflection-c"></a>Yansıma (C#)
Yansıma derlemeleri, modülleri ve türleri <xref:System.Type>tanımlayan nesneler (türü) sağlar. Bir türün örneğini dinamik olarak oluşturmak, türü var olan bir nesneye bağlamak veya var olan bir nesneden türü almak ya da onun yöntemlerini çağırmak ya da alanları ve özelliklerine erişmek için yansıma kullanabilirsiniz. Kodunuzda öznitelikler kullanıyorsanız, yansıma bunlara erişmenizi sağlar. Daha fazla bilgi için bkz. [öznitelikler](../../../standard/attributes/index.md).  
  
 Bir değişkenin türünü almak için `GetType` `Object` temel sınıftan tüm türler tarafından devralınan statik yöntemi kullanan basit bir yansıma örneği aşağıda verilmiştir:  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 Çıktı:  
  
 `System.Int32`  
  
 Aşağıdaki örnek, yüklü derlemenin tam adını almak için yansıma kullanır.  
  
```csharp  
// Using Reflection to get information of an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 Çıktı:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  C# Anahtar sözcükler `protected` ve`internal` Il 'de hiçbir anlamı yoktur ve yansıma API 'lerinde kullanılmaz. Il 'deki ilgili terimler *Aile* ve derlemedir. Yansıma kullanarak bir `internal` yöntemi tanımlamak için <xref:System.Reflection.MethodBase.IsAssembly%2A> özelliğini kullanın. Bir `protected internal` yöntemi tanımlamak için öğesini <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>kullanın.  
  
## <a name="reflection-overview"></a>Yansımaya genel bakış  
 Aşağıdaki durumlarda yansıma yararlı olur:  
  
- Programınızın meta verilerindeki özniteliklere erişmeniz gerektiğinde. Daha fazla bilgi için bkz. [özniteliklerde depolanan bilgileri alma](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
- Bir derlemedeki türleri İnceleme ve örnekleme için.  
  
- Çalışma zamanında yeni türler oluşturmak için. İçinde <xref:System.Reflection.Emit>sınıfları kullanın.  
  
- Geç bağlama gerçekleştirmek için çalışma zamanında oluşturulan türler üzerindeki yöntemlere erişme. [Türleri dinamik olarak yükleme ve kullanma](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)konusuna bakın.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
- [Yansıma](../../../framework/reflection-and-codedom/reflection.md)  
  
- [Tür Bilgilerini Görüntüleme](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [Yansıma ve Genel Türler](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [Özniteliklerde Depolanan Bilgileri Alma](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
