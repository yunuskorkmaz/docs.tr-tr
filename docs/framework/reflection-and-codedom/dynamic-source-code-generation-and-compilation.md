---
title: "Dinamik Kaynak Kodu Oluşturma ve Derleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 535a60aa1a174319a4db3403a64c3998784bbb58
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="dynamic-source-code-generation-and-compilation"></a>Dinamik Kaynak Kodu Oluşturma ve Derleme
Kod belge nesnesi kodun temsil ettiği tek bir modelini temel alan kaynak kodu çalışma zamanında birden çok programlama dillerinde oluşturmak için kaynak kodu yayma programların geliştiriciler sağlayan modeli (CodeDOM) adlı bir mekanizma .NET Framework içerir İşlenecek.  
  
 Kaynak kodu temsil etmek için diğer bazı kaynak kod yapısını modeller CodeDOM grafik bilinen bir veri yapısı oluşturacak şekilde CodeDOM öğeleri bağlanır.  
  
 `System.CodeDom` Ad alanı, belirli bir programlama dilden bağımsız kaynak kodu mantıksal yapısını temsil edebilir türlerini tanımlar. `System.CodeDom.Compiler` Ad alanını kaynak kodu CodeDOM grafikleri oluşturma ve desteklenen dilde kaynak kodu derleme yönetmek için türlerini tanımlar. Desteklenen diller kümesi derleyici satıcılar veya geliştiricilerin genişletebilirsiniz.  
  
 Bir program belirsiz bir hedef dil veya birden çok dilde program modeli için kaynak kodu oluşturmak gerektiğinde dilden bağımsız kaynak kodu modelleme yararlı olabilir. Örneğin, dil desteğini CodeDOM kullanılabilir durumdaysa bazı tasarımcıları doğru programlama dilinde kaynak kodu oluşturmak için bir dil soyutlama arabirimi CodeDOM kullanın.  
  
 .NET Framework kod oluşturucuları ve kod derleyicileri içerir <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, ve <xref:Microsoft.VisualBasic.VBCodeProvider>.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CodeDOM'yi Kullanma](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 Ortak kullanımlar açıklar ve CodeDOM kullanarak basit bir nesne grafik oluşturma gösterir.  
  
 [Kaynak kodu oluşturma ve CodeDOM grafiğinden bir programı derleme](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 Kaynak kodu oluşturma ve içinde tanımlanan sınıflar kullanarak bir dış derleyici ile oluşturulan kod derleme açıklar `System.CodeDom.Compiler` ad alanı.  
  
 [Nasıl yapılır: CodeDOM Kullanarak XML Belge Dosyası Oluşturma](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 XML belgeleri yorumları koduyla oluşturup XML belgeleri çıktısı oluşturur, böylece oluşturulan kod derleme CodeDOM kullanmayı açıklar.  
  
 [Nasıl yapılır: CodeDOM Kullanarak Sınıf Oluşturma](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 CodeDOM alanları, özellikleri, bir yöntemi, bir oluşturucu ve bir giriş noktası içeren bir sınıf oluşturmak için nasıl kullanılacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.CodeDom>  
 Kod öğeleri programlama dillerinde hedefleyen ortak dil çalışma zamanı temsil eden öğeleri tanımlar.  
  
 <xref:System.CodeDom.Compiler>  
 Kodu oluşturma ve çalışma zamanında derleme için arabirimi tanımlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [CodeDOM hızlı başvuru](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 Geliştiricilerin kaynak kod öğeleri temsil eden CodeDOM öğeleri bulmak hızlı bir yol sağlar.
