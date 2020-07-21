---
title: Dinamik Kaynak Kodu Oluşturma ve Derleme
description: Kod Belge Nesne Modeli (CodeDOM) ile .NET 'te dinamik kaynak kodu derleyin ve oluşturun. CodeDOM öğeleri, CodeDOM grafiği oluşturacak şekilde bağlantılıdır.
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
ms.openlocfilehash: 3cdd89ac9745f6af133ca683afff64283f2727d1
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475105"
---
# <a name="compile-and-generate-dynamic-source-code"></a>Derleme ve dinamik kaynak kodu oluşturma

.NET Framework, kaynak kodu oluşturan program geliştiricilerinin, işlenecek kodu temsil eden tek bir modele göre çalışma zamanında birden fazla programlama dilinde kaynak kodu oluşturmasını sağlayan Kod Belge Nesne Modeli (CodeDOM) adlı bir mekanizma içerir.  
  
Kaynak kodunu temsil etmek için CodeDOM öğeleri birbirlerine bağlanır ve bu, bazı kaynak kodların yapısını modelleyen, CodeDOM grafiği olarak bilinen bir veri yapısı oluşturur.  
  
<xref:System.CodeDom?displayProperty=fullName>Ad alanı, belirli bir programlama dilinden bağımsız olarak kaynak kodun mantıksal yapısını temsil eden türleri tanımlar. <xref:System.CodeDom.Compiler?displayProperty=fullName>Ad alanı, CodeDOM grafiklerinden kaynak kodu oluşturmak ve desteklenen dillerde kaynak kodu derlemesini yönetmek için türleri tanımlar. Derleyici satıcıları veya geliştiriciler desteklenen dillerin kümesini genişletebilir.  
  
Dilden bağımsız kaynak kodu modelleme, bir programın birden çok dilde veya belirsiz bir hedef dil için bir program modeli için kaynak kodu oluşturması gerektiğinde değerli olabilir. Örneğin, bazı tasarımcılar, kaynak kodu doğru programlama dilinde oluşturmak için CodeDOM 'yi bir dil soyutlama arabirimi olarak kullanır, bu dil için CodeDOM desteği kullanılabilir.  
  
.NET Framework,, ve için kod oluşturucuları ve kod derleyicileri içerir <xref:Microsoft.CSharp.CSharpCodeProvider> <xref:Microsoft.JScript.JScriptCodeProvider> <xref:Microsoft.VisualBasic.VBCodeProvider> .  
  
## <a name="in-this-section"></a>Bu bölümde

- [CodeDOM'yi Kullanma](using-the-codedom.md)

  Ortak kullanımları açıklar ve CodeDOM kullanılarak basit nesne grafı oluşturmayı gösterir.  
  
- [Bir CodeDOM grafiğinden kaynak kodu oluşturma ve bir programı derleme](generating-and-compiling-source-code-from-a-codedom-graph.md)  

  Kaynak kodu oluşturmayı ve ad alanında tanımlanan sınıfları kullanarak oluşturulan kodu bir dış derleyici ile derlemeyi açıklar `System.CodeDom.Compiler` .  
  
- [Nasıl yapılır: CodeDOM Kullanarak XML Belge Dosyası Oluşturma](how-to-create-an-xml-documentation-file-using-codedom.md)  

  XML belge açıklamalarıyla kod oluşturmak için CodeDOM kullanmayı ve XML belge çıkışını oluşturacak şekilde oluşturulan kodu derlemeyi açıklar.  
  
- [Nasıl yapılır: CodeDOM Kullanarak Sınıf Oluşturma](how-to-create-a-class-using-codedom.md)  

  Alanları, özellikleri, bir yöntemi, oluşturucuyu ve bir giriş noktasını içeren bir sınıf oluşturmak için CodeDOM nasıl kullanacağınızı açıklar.  
  
## <a name="reference"></a>Başvuru  

- <xref:System.CodeDom>  

  Ortak dil çalışma zamanını hedefleyen programlama dillerinde kod öğelerini temsil eden öğeleri tanımlar.  
  
- <xref:System.CodeDom.Compiler>  

  Çalışma zamanında kod oluşturma ve derleme için arabirimler tanımlar.  
  
## <a name="related-sections"></a>İlgili bölümler  

- [CodeDOM hızlı başvurusu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)) , geliştiricilerin kaynak kodu öğelerini temsil eden CodeDOM öğelerini bulmasını sağlayan hızlı bir yol sağlar.
