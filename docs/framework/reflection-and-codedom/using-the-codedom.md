---
title: CodeDOM'yi Kullanma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cd2b8e8ecb0e5d451ebf3c6823144e4a90e0d79
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="using-the-codedom"></a>CodeDOM'yi Kullanma
CodeDOM genel türlerde kaynak kod öğeleri temsil eden türler sağlar. Bir nesne grafiğinin derlemek için CodeDOM öğeleri kullanılarak bir kaynak kod modeli derlemeler bir program tasarlayabilirsiniz. Bu nesne grafiği, kaynak kodu CodeDOM Kod Oluşturucu için desteklenen bir programlama dili kullanılarak oluşturulabilir. CodeDOM ikili derlemeye kaynak kodu derlemek için de kullanılabilir.  
  
 CodeDOM için bazı yaygın kullanımları şunlardır:  
  
-   Şablonlu kod oluşturma: ASP.NET, XML Web Hizmetleri istemci proxy'leri, kod sihirbazları, tasarımcıları veya diğer kod yayma mekanizmaları için kod oluşturma.  
  
-   Dinamik derleme: tek veya birden çok dil kodu derleme destekleme.  
  
## <a name="building-a-codedom-graph"></a>CodeDOM grafik oluşturma  
 <xref:System.CodeDom> Ad alanı dili sözdizimini bağımsız kaynak kodu mantıksal yapısını temsil eden sınıflar sağlar.  
  
### <a name="the-structure-of-a-codedom-graph"></a>CodeDOM grafik yapısı  
 CodeDOM grafik kapsayıcıları ağacının gibi yapısıdır. En üstteki, veya kök, kapsayıcı her derlenebilir CodeDOM grafiğin bir <xref:System.CodeDom.CodeCompileUnit>. Kaynak kodu modelinizin her öğenin özelliği aracılığıyla grafiği içine bağlanmalıdır bir <xref:System.CodeDom.CodeObject> grafikte.  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a>Bir kaynak kod modeli için bir örnek Hello World Program oluşturma  
 Aşağıdaki örneklerde, basit bir Hello World uygulamasının kodunu temsil eden bir CodeDOM Nesne grafiği oluşturmak nasıl bir örnek sağlar. Bu kod örneği için tam kaynak kodunu için bkz: <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> konu.  
  
#### <a name="creating-a-compile-unit"></a>Derleme birimi oluşturma  
 CodeDOM adlı bir nesne tanımlayan bir <xref:System.CodeDom.CodeCompileUnit>, hangi derlemek için kaynak kodu modelleri CodeDOM nesne grafiğinin başvuru. A **CodeCompileUnit** öznitelikler, ad alanları ve derlemeler başvurularını depolamak için özelliklere sahiptir.  
  
 Öğesinden türetilen CodeDom sağlayıcıları <xref:System.CodeDom.Compiler.CodeDomProvider> sınıfı tarafından başvurulan nesne grafiği işleme yöntemleri içeren bir **CodeCompileUnit**.  
  
 Basit bir uygulama için bir nesne grafiğinin oluşturmak için kaynak kod modeli derlemek ve ondan başvuran bir **CodeCompileUnit**.  
  
 Bu örnekte gösterilen sözdizimi ile yeni bir derleme birimi oluşturabilirsiniz:  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 A <xref:System.CodeDom.CodeSnippetCompileUnit> bir bölümünü zaten hedef dilde olan ancak başka bir dilde işlenemiyor. kaynak kodu içerebilir.  
  
#### <a name="defining-a-namespace"></a>Bir ad alanı tanımlama  
 Bir ad alanı tanımlamak üzere oluşturma bir <xref:System.CodeDom.CodeNamespace> ve uygun oluşturucuyu kullanarak veya ayarlayarak bir ad atayın kendi **adı** özelliği.  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a>Bir ad alanı içe aktarma  
 Ad alanına ad alanı içe aktarma yönergesi eklemek için Ekle bir <xref:System.CodeDom.CodeNamespaceImport> almak için ad alanı gösterir **CodeNamespace.Imports** koleksiyonu.  
  
 Alma için aşağıdaki kodu ekler **sistem** ad alanına **içeri aktarmalar** koleksiyonu bir **CodeNamespace** adlı `samples`:  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a>Nesne grafiği kod öğeleri bağlama  
 CodeDOM grafik form tüm kod öğeleri bağlanması <xref:System.CodeDom.CodeCompileUnit> diğer bir deyişle başvuruları doğrudan kök nesnesi grafik özelliklerinden başvuru öğeler arasında bir dizi ağacın kök öğesi. Kapsayıcı nesne başvurusundan kurmak için bir kapsayıcı nesnesinin bir özellik için bir nesne ayarlayın.  
  
 Aşağıdaki deyim ekler `samples` **CodeNamespace** için **ad alanları** koleksiyon özelliği kök **CodeCompileUnit**.  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a>Bir türü tanımlama  
 Bir sınıf, yapı, arabirimi ya da CodeDOM kullanarak numaralandırması bildirmek için yeni bir oluşturma <xref:System.CodeDom.CodeTypeDeclaration>ve bir ad atayın. Aşağıdaki örnekte bu ayarlamak için bir oluşturucu aşırı kullanmayı gösterir. **adı** özelliği:  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 Bir tür için bir ad eklemek için Ekle bir <xref:System.CodeDom.CodeTypeDeclaration> ad alanına eklemek için türünü temsil eden **türleri** koleksiyonu bir **CodeNamespace**.  
  
 Aşağıdaki örnek adlı bir sınıf eklemek gösterilmiştir `class1` için bir **CodeNamespace** adlı `samples`:  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a>Sınıf üyeleri için sınıf ekleme  
 <xref:System.CodeDom> Ad alanı, sınıf üyeleri temsil etmek için kullanılan öğelerin çeşitli sağlar. Her sınıf üyesi eklenebilir **üyeleri** koleksiyonu bir <xref:System.CodeDom.CodeTypeDeclaration>.  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a>Yürütülebilir bir dosya için bir kod giriş noktası yöntem tanımlama  
 Kod bir yürütülebilir programı için oluşturuluyorsa oluşturarak bir programın giriş noktasını belirtmek gerekli olan bir <xref:System.CodeDom.CodeEntryPointMethod> program yürütme başlamalıdır yöntemi temsil etmek için.  
  
 Aşağıdaki örnek içeren bir giriş noktası yöntemi tanımlamak gösterilmiştir bir <xref:System.CodeDom.CodeMethodInvokeExpression> çağrısı **System.Console.WriteLine** "Hello World!" yazdırmak için:  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 Aşağıdaki deyim adlı giriş noktası yöntemi ekler `Start` için **üyeleri** koleksiyonu `class1`:  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 Şimdi <xref:System.CodeDom.CodeCompileUnit> adlı `compileUnit` basit bir Hello World program CodeDOM grafik içeriyor. CodeDOM grafiğinden kodu oluşturma ve derleme hakkında daha fazla bilgi için bkz: [kaynak kodu oluşturma ve CodeDOM grafiğinden programını derleme](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).  
  
### <a name="more-information-on-building-a-codedom-graph"></a>CodeDOM grafik oluşturma hakkında daha fazla bilgi  
 CodeDOM ortak dil çalışma zamanı desteği programlama dillerinde bulunan kod öğeleri birçok ortak türlerini destekler. CodeDOM tüm olası programlama dil özelliklerini temsil etmek için öğeleri sağlamak için tasarlanmamıştır. CodeDOM öğeleriyle kolayca gösterilemez kodu kapsüllenmiş içinde bir <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember>, veya bir <xref:System.CodeDom.CodeSnippetCompileUnit>. Ancak, parçacıkları diğer diller için otomatik olarak CodeDOM tarafından çevrilemiyor.  
  
 CodeDOM türlerinin her belge için başvuru belgelerine bakın <xref:System.CodeDom> ad alanı.  
  
 Kod öğesi belirli bir türü temsil eden CodeDOM öğesi bulmak hızlı grafiği için bkz: [CodeDOM hızlı başvuru](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524).
