---
title: CodeDOM'yi Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- Code Document Object Model
- Code Document Object Model, graphs
- types, CodeDOM
- namespaces [.NET Framework], CodeDOM
- templated code generation
- dynamically representing source code
- source code models
- CodeDOM
- graphing with CodeDOM
- dynamic compilation
- code generators
- CodeDOM, graphs
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56b0b76e8dc137cbb9346f97604c2d53435c1fe6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045738"
---
# <a name="using-the-codedom"></a>CodeDOM'yi Kullanma
CodeDOM birçok ortak kaynak kodu öğesi türünü temsil eden türler sağlar. Bir nesne grafiğini birleştirmek için CodeDOM öğelerini kullanarak kaynak kodu modeli oluşturan bir program tasarlayabilirsiniz. Bu nesne grafiği, desteklenen bir programlama dili için CodeDOM Kod Oluşturucu kullanılarak kaynak kodu olarak oluşturulabilir. CodeDOM, kaynak kodu ikili bir derlemeye derlemek için de kullanılabilir.  
  
 CodeDOM için bazı yaygın kullanımlar şunlardır:  
  
- Şablonlu kod oluşturma: ASP.NET, XML Web Hizmetleri istemci proxy 'leri, kod sihirbazları, tasarımcılar veya diğer kod yayma mekanizmaları için kod üretme.  
  
- Dinamik derleme: kod derlemesini tek veya birden çok dilde destekleme.  
  
## <a name="building-a-codedom-graph"></a>CodeDOM grafiği oluşturma  
 <xref:System.CodeDom> Ad alanı, dil sözdiziminden bağımsız olarak kaynak kodun mantıksal yapısını temsil eden sınıflar sağlar.  
  
### <a name="the-structure-of-a-codedom-graph"></a>CodeDOM grafiğinin yapısı  
 CodeDOM grafiğinin yapısı bir kapsayıcı ağacı gibidir. Her bir derlenebilir CodeDOM grafiğinin en üst, veya kök kapsayıcısı bir <xref:System.CodeDom.CodeCompileUnit>. Kaynak kodu modelinizdeki her öğe, grafikteki bir <xref:System.CodeDom.CodeObject> öğesinin özelliği aracılığıyla grafiğe bağlanmalıdır.  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a>Örnek bir Merhaba Dünya program için kaynak kodu modeli oluşturma  
 Aşağıdaki izlenecek yol, basit bir Merhaba Dünya uygulaması için kodu temsil eden bir CodeDOM nesne grafiğinin nasıl derlendiğini gösteren bir örnek sağlar. Bu kod örneği için tüm kaynak kodu için konusuna bakın <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> .  
  
#### <a name="creating-a-compile-unit"></a>Derleme birimi oluşturma  
 CodeDom, kaynak kodu derlemek için modelleyen bir CodeDOM nesne grafiğine başvuruda bulunan, adlı bir <xref:System.CodeDom.CodeCompileUnit>nesneyi tanımlar. **CodeCompileUnit** , başvuruları özniteliklere, ad alanlarına ve derlemelere depolamaya yönelik özelliklere sahiptir.  
  
 <xref:System.CodeDom.Compiler.CodeDomProvider> Sınıfından türetilen CodeDom sağlayıcıları, bir **CodeCompileUnit**tarafından başvurulan nesne grafiğini işleyen yöntemler içerir.  
  
 Basit bir uygulama için bir nesne grafiği oluşturmak için, kaynak kodu modelini oluşturmanız ve bir **CodeCompileUnit**öğesinden başvurmanız gerekir.  
  
 Bu örnekte gösterilen sözdizimi ile yeni bir derleme birimi oluşturabilirsiniz:  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <xref:System.CodeDom.CodeSnippetCompileUnit> , Kaynak kodun zaten hedef dilde olan bir bölümünü içerebilir, ancak başka bir dile işlenemez.  
  
#### <a name="defining-a-namespace"></a>Ad alanı tanımlama  
 Bir ad alanı tanımlamak için, uygun <xref:System.CodeDom.CodeNamespace> oluşturucuyu kullanarak veya **ad** özelliğini ayarlayarak bir ad oluşturun ve buna bir ad atayın.  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a>Ad alanı içeri aktarma  
 Ad alanına içeri aktarma yönergesi eklemek için, **CodeNamespace. Imports** koleksiyonuna <xref:System.CodeDom.CodeNamespaceImport> aktarılacak ad alanını belirten bir ekleyin.  
  
 Aşağıdaki kod, **sistem** ad alanı için adlı `samples`bir **CodeNamespace** **Imports** koleksiyonuna bir içeri aktarma ekler:  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a>Kod öğelerini nesne grafiğine bağlama  
 CodeDOM grafiği oluşturan tüm kod öğeleri, <xref:System.CodeDom.CodeCompileUnit> grafiğin kök nesnesinin özelliklerinden doğrudan başvurulan öğeler arasında bir dizi başvuruya göre ağacın kök öğesi olan ile bağlantılı olmalıdır. Container nesnesinden bir başvuru oluşturmak için bir nesneyi kapsayıcı nesnesinin özelliğine ayarlayın.  
  
 Aşağıdaki ifade, **CodeNamespace** öğesini `samples` kök **CodeCompileUnit**öğesinin **namespaces** koleksiyon özelliğine ekler.  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a>Bir tür tanımlama  
 CodeDOM kullanarak bir sınıf, yapı, arabirim veya sabit listesi bildirmek için yeni <xref:System.CodeDom.CodeTypeDeclaration>bir oluşturun ve bir ad atayın. Aşağıdaki örnek, **ad** özelliğini ayarlamak için bir Oluşturucu aşırı yüklemesi kullanarak bunu gösterir:  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 Bir ad alanına bir tür eklemek için, bir <xref:System.CodeDom.CodeTypeDeclaration> **CodeNamespace** **Types** koleksiyonuna ad alanına eklenecek türü temsil eden bir ekleyin.  
  
 Aşağıdaki örnek adlı `class1` `samples`bir **CodeNamespace** adlı sınıfın nasıl ekleneceğini göstermektedir:  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a>Sınıf üyelerini bir sınıfa ekleme  
 Ad <xref:System.CodeDom> alanı, sınıf üyelerini temsil etmek için kullanılabilecek çeşitli öğeler sağlar. Her sınıf üyesi bir <xref:System.CodeDom.CodeTypeDeclaration>öğesinin **Üyeler** koleksiyonuna eklenebilir.  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a>Yürütülebilir dosya için kod giriş noktası yöntemi tanımlama  
 Yürütülebilir bir program için kod oluşturuyorsanız, program yürütmenin başlayacağı yöntemi temsil edecek bir <xref:System.CodeDom.CodeEntryPointMethod> programın giriş noktasını göstermek gerekir.  
  
 Aşağıdaki örnek, "Merhaba Dünya!" yazdırmak için <xref:System.CodeDom.CodeMethodInvokeExpression> **System. Console. WriteLine** çağıran bir içeren bir giriş noktası yönteminin nasıl tanımlanacağını göstermektedir:  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 Aşağıdaki ifade, öğesinin `Start` `class1` **Üyeler** koleksiyonuna adlı giriş noktası yöntemini ekler:  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <xref:System.CodeDom.CodeCompileUnit> Şimdi adlandırılmış `compileUnit` bir basit Merhaba Dünya program için CodeDOM grafiğini içerir. CodeDOM grafiğinden kod oluşturma ve derleme hakkında daha fazla bilgi için bkz. [kaynak kodu oluşturma ve bir CodeDOM grafiğinden program derleme](generating-and-compiling-source-code-from-a-codedom-graph.md).  
  
### <a name="more-information-on-building-a-codedom-graph"></a>CodeDOM grafiği oluşturma hakkında daha fazla bilgi  
 CodeDOM, ortak dil çalışma zamanını destekleyen programlama dillerinde bulunan birçok ortak kod öğesi türünü destekler. CodeDOM, tüm olası programlama dili özelliklerini temsil eden öğeler sağlamak üzere tasarlanmamıştır. CodeDOM öğeleriyle kolayca gösterilemeyen <xref:System.CodeDom.CodeSnippetExpression>kod, bir, <xref:System.CodeDom.CodeSnippetStatement> <xref:System.CodeDom.CodeSnippetCompileUnit>, <xref:System.CodeDom.CodeSnippetTypeMember>, veya şeklinde kapsüllenebilir. Ancak, kod parçacıkları CodeDOM tarafından otomatik olarak diğer dillere çevrilemez.  
  
 CodeDOM türlerinin her biri için belgeler için bkz. <xref:System.CodeDom> ad alanı için başvuru belgeleri.  
  
 Belirli bir kod öğesi türünü temsil eden CodeDOM öğesini bulmak için hızlı bir grafik için, [CodeDOM hızlı başvurusuna](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))bakın.
