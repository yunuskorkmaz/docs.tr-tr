---
title: Dinamik Kaynak Kodu Oluşturma ve Derleme
ms.date: 03/30/2017
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a90b4214e244bc1f9c5f8e71782e604bd6c7b619
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494245"
---
# <a name="dynamic-source-code-generation-and-compilation"></a>Dinamik Kaynak Kodu Oluşturma ve Derleme
.NET Framework kod belge nesne geliştiricilerin kodunu temsil eden tek bir modelini temel alan kaynak kodu, çalışma zamanında birden fazla programlama dilinde oluşturmak için kaynak kodu yayma programlar sağlayan modeli (CodeDOM) adlı bir mekanizma içerir İşlenecek.  
  
 Kaynak kodu temsil etmek için diğer bazı kaynak kodunun yapısını modeller CodeDOM grafiği bilinen bir veri yapısı oluşturmak için CodeDOM öğelerini bağlıdır.  
  
 `System.CodeDom` Ad alanı, kaynak kodu, belirli bir programlama dilini bağımsız mantıksal yapısını temsil edebilen türleri tanımlar. `System.CodeDom.Compiler` CodeDOM grafiklerinden kaynak kodu oluşturma ve derleme desteklenen dilde kaynak kodu yönetmek için ad alanını tanımlayan tür. Derleyici satıcılar veya geliştiricilerin desteklenen dil kümesini genişletebilirsiniz.  
  
 Birden çok dilde bir program modeli için veya belirsiz bir hedef dil için kaynak kodu oluşturmak bir program gerektiğinde dilden bağımsız kaynak kodu modelleme yararlı olabilir. Örneğin, dil desteğini CodeDOM varsa bazı tasarımcıları doğru programlama dilinde, kaynak kodunu üretmek için bir dil soyutlama arabirimi CodeDOM kullanın.  
  
 .NET Framework kod oluşturucuları ve için kod derleyicileri içerir <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, ve <xref:Microsoft.VisualBasic.VBCodeProvider>.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CodeDOM'yi Kullanma](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 Yaygın kullanımları açıklar ve CodeDOM kullanarak bir Basit Nesne grafiği oluşturmayı göstermektedir.  
  
 [Kaynak kodu üretme ve CodeDOM grafiğinden bir programı derleme](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 Kaynak kodu oluşturun ve oluşturulan kod içinde tanımlanan sınıflar kullanarak dış bir derleyici ile derleme açıklar `System.CodeDom.Compiler` ad alanı.  
  
 [Nasıl yapılır: CodeDOM Kullanarak XML Belge Dosyası Oluşturma](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 XML belgeleri açıklamaları olan kod oluşturma ve XML belgeleri çıktısı oluşturması oluşturulan kodu derlemek için CodeDOM kullanmayı açıklar.  
  
 [Nasıl yapılır: CodeDOM Kullanarak Sınıf Oluşturma](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 CodeDOM alanlar, özellikler, bir yöntem, bir oluşturucu ve bir giriş noktası içeren bir sınıf oluşturmak için nasıl kullanılacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.CodeDom>  
 Ortak dil çalışma zamanını hedefleyen programlama dillerinde kod öğelerini temsil eden öğelerini tanımlar.  
  
 <xref:System.CodeDom.Compiler>  
 Arabirimleri oluşturma ve çalışma zamanında kod derlemek için tanımlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [CodeDOM hızlı başvuru](https://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 Kaynak kod öğelerini temsil eden CodeDOM öğeleri bulmak, geliştiriciler için hızlı bir yol sağlar.
