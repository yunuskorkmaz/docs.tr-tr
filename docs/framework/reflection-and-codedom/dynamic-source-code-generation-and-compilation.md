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
ms.openlocfilehash: 5fb95ab7ff4fcac7169238d90637d7b83078d6dd
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046113"
---
# <a name="dynamic-source-code-generation-and-compilation"></a>Dinamik Kaynak Kodu Oluşturma ve Derleme
.NET Framework, kaynak kodu oluşturan program geliştiricilerinin, kodu temsil eden tek bir modele göre, çalışma zamanında birden çok programlama dilinde kaynak kodu oluşturmasını sağlayan Kod Belge Nesne Modeli (CodeDOM) adlı bir mekanizma içerir işlemek için.  
  
 Kaynak kodunu temsil etmek için CodeDOM öğeleri birbirlerine bağlanır ve bu, bazı kaynak kodların yapısını modelleyen, CodeDOM grafiği olarak bilinen bir veri yapısı oluşturur.  
  
 Ad `System.CodeDom` alanı, belirli bir programlama dilinden bağımsız olarak kaynak kodun mantıksal yapısını temsil eden türleri tanımlar. Ad `System.CodeDom.Compiler` alanı, CodeDOM grafiklerinden kaynak kodu oluşturmak ve desteklenen dillerde kaynak kodu derlemesini yönetmek için türleri tanımlar. Derleyici satıcıları veya geliştiriciler desteklenen dillerin kümesini genişletebilir.  
  
 Dilden bağımsız kaynak kodu modelleme, bir programın birden çok dilde veya belirsiz bir hedef dil için bir program modeli için kaynak kodu oluşturması gerektiğinde değerli olabilir. Örneğin, bazı tasarımcılar, kaynak kodu doğru programlama dilinde oluşturmak için CodeDOM 'yi bir dil soyutlama arabirimi olarak kullanır, bu dil için CodeDOM desteği kullanılabilir.  
  
 .NET Framework,, ve <xref:Microsoft.CSharp.CSharpCodeProvider> <xref:Microsoft.JScript.JScriptCodeProvider> <xref:Microsoft.VisualBasic.VBCodeProvider>için kod oluşturucuları ve kod derleyicileri içerir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CodeDOM'yi Kullanma](using-the-codedom.md)  
 Ortak kullanımları açıklar ve CodeDOM kullanılarak basit nesne grafı oluşturmayı gösterir.  
  
 [Kaynak kodu oluşturma ve bir CodeDOM grafiğinden program derleme](generating-and-compiling-source-code-from-a-codedom-graph.md)  
 Kaynak kodu oluşturmayı ve `System.CodeDom.Compiler` ad alanında tanımlanan sınıfları kullanarak oluşturulan kodu bir dış derleyici ile derlemeyi açıklar.  
  
 [Nasıl yapılır: CodeDOM kullanarak XML belge dosyası oluşturma](how-to-create-an-xml-documentation-file-using-codedom.md)  
 XML belge açıklamalarıyla kod oluşturmak için CodeDOM kullanmayı ve XML belge çıkışını oluşturacak şekilde oluşturulan kodu derlemeyi açıklar.  
  
 [Nasıl yapılır: CodeDOM kullanarak sınıf oluşturma](how-to-create-a-class-using-codedom.md)  
 Alanları, özellikleri, bir yöntemi, oluşturucuyu ve bir giriş noktasını içeren bir sınıf oluşturmak için CodeDOM nasıl kullanacağınızı açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.CodeDom>  
 Ortak dil çalışma zamanını hedefleyen programlama dillerinde kod öğelerini temsil eden öğeleri tanımlar.  
  
 <xref:System.CodeDom.Compiler>  
 Çalışma zamanında kod oluşturma ve derleme için arabirimler tanımlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [CodeDOM hızlı başvurusu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))  
 Geliştiricilerin kaynak kodu öğelerini temsil eden CodeDOM öğelerini bulması için hızlı bir yol sağlar.
