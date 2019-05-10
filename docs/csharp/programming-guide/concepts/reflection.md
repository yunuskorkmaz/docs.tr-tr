---
title: Yansıma (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4593aeef13f5d1d0c223b40e266556cb2bcfee5f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595546"
---
# <a name="reflection-c"></a>Yansıma (C#)
Yansıma nesneleri sağlar (tür <xref:System.Type>) derlemeler, modüller ve türler açıklanmaktadır. Yansıma, dinamik olarak bir türün bir örneğini oluşturmak, bağlama türü var olan bir nesneye veya türü mevcut bir nesneden elde ve kendi yöntemlerini çağırmak veya kendi alanlarına ve özelliklerine erişmek için kullanabilirsiniz. Kodunuzda öznitelikler kullanıyorsanız, yansıma erişim sağlar. Daha fazla bilgi için [öznitelikleri](../../../../docs/standard/attributes/index.md).  
  
 Yansıma statik bir yöntemi kullanarak basit bir örnek `GetType` - tüm türleri tarafından devralınan `Object` temel sınıfı - bir değişken türü elde etmek için:  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 Çıktı.  
  
 `System.Int32`  
  
 Aşağıdaki örnek, yüklü bütünleştirilmiş kodun tam adı almak için yansıtma kullanır.  
  
```csharp  
// Using Reflection to get information of an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 Çıktı.  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  C# anahtar sözcükleri `protected` ve `internal` IL içinde herhangi bir anlamı yoktur ve yansıma API'leri kullanılmaz. IL içinde karşılık gelen terimlerdir *ailesi* ve *derleme*. Tanımlamak için bir `internal` yansıma, kullanım kullanarak yöntemi <xref:System.Reflection.MethodBase.IsAssembly%2A> özelliği. Tanımlamak için bir `protected internal` yöntemi, kullanım <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.  
  
## <a name="reflection-overview"></a>Yansıma genel bakış  
 Yansıma, aşağıdaki durumlarda kullanışlıdır:  
  
- Programınızın meta veri öznitelikleri erişmeye olduğunda. Daha fazla bilgi için [öznitelikleri depolanan alınırken bilgi](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
- İnceleme ve derlemedeki türleri örnekleme için.  
  
- Çalışma zamanında yeni türler oluşturmak için. Sınıfları kullanın <xref:System.Reflection.Emit>.  
  
- Çalışma zamanında oluşturulan türlerde yöntemleri erişme geç bağlama gerçekleştirmek için. Konusuna [dinamik olarak yükleme ve türleri kullanarak](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
- [Yansıma](../../../framework/reflection-and-codedom/reflection.md)  
  
- [Tür Bilgilerini Görüntüleme](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [Yansıma ve Genel Türler](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [Özniteliklerde Depolanan Bilgileri Alma](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
