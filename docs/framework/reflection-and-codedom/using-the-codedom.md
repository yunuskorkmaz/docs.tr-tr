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
ms.openlocfilehash: 73810330c1ec44aa3a5edf47b3062bc2df267008
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792983"
---
# <a name="using-the-codedom"></a>CodeDOM'yi Kullanma
CodeDOM, kaynak kod öğelerinin birçok ortak türleri temsil eden türler sağlar. Bir nesne grafiğini derlemek için CodeDOM öğelerini kullanarak bir kaynak kod modeli oluşturan bir program tasarlayabilirsiniz. Bu nesne grafiği, desteklenen bir programlama dili için bir CodeDOM kod üreticisi kullanan bir kaynak kodu olarak işlenebilir. CodeDOM, kaynak kodu ikili bir birleştirme dosyasına derlemek için de kullanılabilir.  
  
 CodeDOM bazı yaygın kullanımları şunlardır:  
  
- Şablonlu kod oluşturma: ASP.NET, XML Web Hizmetleri istemci proxy'leri, kod sihirbazları, tasarımcılar veya diğer kod yayan mekanizmaları için kod oluşturma.  
  
- Dinamik derleme: tek veya birden çok dilde kod derlemesini destekleme.  
  
## <a name="building-a-codedom-graph"></a>CodeDOM grafiği derleme  
 <xref:System.CodeDom> Ad alanı dil sözdiziminden bağımsız kaynak kodu mantıksal yapısını temsil etmek için sınıflar sağlar.  
  
### <a name="the-structure-of-a-codedom-graph"></a>CodeDOM grafiği yapısı  
 CodeDOM grafiği yapısı, bir kapsayıcılar ağacı gibidir ' dir. En üstteki veya kök, her bir derlenebilir CodeDOM grafiğinin kapsayıcı bir <xref:System.CodeDom.CodeCompileUnit>. Her öğenin kaynak kod modelinizin özelliği ile grafikle bağlanmalıdır bir <xref:System.CodeDom.CodeObject> grafiğinde.  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a>Örnek Hello World programı için bir kaynak kod modeli oluşturma  
 Aşağıdaki örneklerde, basit bir Hello World uygulaması kodunu temsil eden bir CodeDOM nesne grafiğinin nasıl bir örnek sağlar. Bu kod örneği için tam kaynak kodunu görmek <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> konu.  
  
#### <a name="creating-a-compile-unit"></a>Derleme birimi oluşturma  
 CodeDOM adlı bir nesne tanımlayan bir <xref:System.CodeDom.CodeCompileUnit>, derlenecek kaynağı modelleyen bir CodeDOM nesnesi grafiğine başvurabilir. A **CodeCompileUnit** başvuruları özniteliklere, ad alanları ve derlemelere depolama özelliklerine sahiptir.  
  
 Öğesinden türetilen CodeDom sağlayıcıları <xref:System.CodeDom.Compiler.CodeDomProvider> sınıfı tarafından başvurulan nesne grafiğini işleyen yöntemleri içeren bir **CodeCompileUnit**.  
  
 Basit bir uygulama için bir nesne grafiği oluşturmak için kaynak kod modelini bir araya getirmeli ve ondan başvuru bir **CodeCompileUnit**.  
  
 Bu örnekte gösterilen sözdizimi ile yeni bir derleme birimi oluşturabilirsiniz:  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 A <xref:System.CodeDom.CodeSnippetCompileUnit> hedef dilde zaten olan ancak başka bir dile işlenemeyen kaynak kodunun bir bölüm içerebilir.  
  
#### <a name="defining-a-namespace"></a>Ad alanı tanımlama  
 Ad alanı tanımlamak için oluşturun bir <xref:System.CodeDom.CodeNamespace> ve uygun oluşturucuyu kullanarak veya ayarlayarak bir ad atayın, **adı** özelliği.  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a>Bir ad alanı alma  
 Ad alanı için bir ad alanı içe aktarma yönergesi eklemek için Ekle bir <xref:System.CodeDom.CodeNamespaceImport> almak için ad alanı belirten **CodeNamespace.Imports** koleksiyonu.  
  
 Aşağıdaki kod bir içe aktarım ekler **sistem** ad alanına **içeri aktarmalar** koleksiyonunu bir **CodeNamespace** adlı `samples`:  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a>Kod öğelerini nesne grafiğine bağlama  
 CodeDOM grafiği oluşturan tüm kod öğelerini bağlanmalıdır <xref:System.CodeDom.CodeCompileUnit> diğer bir deyişle başvuruları grafiğin kök nesnesinin özelliklerinden doğrudan başvurulan öğeler arasındaki bir dizi göre ağacın kök öğe. Bir nesneyi kapsayıcı nesnenin bir başvuru oluşturmak için bir kapsayıcı nesnenin bir özelliğini ayarlayın.  
  
 Aşağıdaki deyimi ekler `samples` **CodeNamespace** için **ad alanları** koleksiyon özelliği kök **CodeCompileUnit**.  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a>Türü tanımlama  
 Bir sınıf, yapı, arabirimi ya da CodeDOM kullanarak numaralandırma bildirmek için yeni bir oluşturma <xref:System.CodeDom.CodeTypeDeclaration>ve bir ad atayın. Aşağıdaki örnek bu ayarlamak için bir yapıcı yeniden yüklemesi kullanarak göstermektedir **adı** özelliği:  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 Bir tür için bir ad alanı eklemek için Ekle bir <xref:System.CodeDom.CodeTypeDeclaration> ad alanına eklenecek türünü temsil eden **türleri** koleksiyonunu bir **CodeNamespace**.  
  
 Aşağıdaki örnekte adlı bir sınıf eklemek gösterilmiştir `class1` için bir **CodeNamespace** adlı `samples`:  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a>Sınıf üyeleri ekleme  
 <xref:System.CodeDom> Ad alanı sınıf üyelerini temsil etmek için kullanılan öğeleri çeşitli sağlar. Her sınıf üyesi eklenebilir **üyeleri** koleksiyonunu bir <xref:System.CodeDom.CodeTypeDeclaration>.  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a>Bir yürütülebilir dosya için bir kod girişi noktası yönetimini tanımlama  
 Yürütülebilir program kodunu oluşturuyorsanız oluşturarak programın giriş noktasını belirtmek gerekli bir <xref:System.CodeDom.CodeEntryPointMethod> , program yürütmenin başlaması gerektiği yöntemi temsil edecek.  
  
 Aşağıdaki örnek içeren bir giriş noktası yönteminin nasıl tanımlanacağını gösterir bir <xref:System.CodeDom.CodeMethodInvokeExpression> çağrılarının **System.Console.WriteLine** "Hello World!" yazdırmak için:  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 Aşağıdaki deyim adlı giriş noktası yöntemi eklemektedir `Start` için **üyeleri** koleksiyonunu `class1`:  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 Artık <xref:System.CodeDom.CodeCompileUnit> adlı `compileUnit` basit bir Hello World programı için CodeDOM grafiğini içerir. CodeDOM grafiğinden kodu oluşturma ve derleme hakkında daha fazla bilgi için bkz: [kaynak kodu üretme ve CodeDOM grafiğinden bir programı derleme](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).  
  
### <a name="more-information-on-building-a-codedom-graph"></a>CodeDOM grafik oluşturma hakkında daha fazla bilgi  
 CodeDOM kod öğeleri, ortak dil çalışma zamanını destekleyen programlama dillerinde bulunan pek çok ortak türlerini destekler. CodeDOM, olası programlama dili özelliklerini temsil edecek öğeleri sağlamak üzere tasarlanmamıştır. CodeDOM öğeleri ile kolayca gösterilemeyen kod, içinde kapsüllenebilir bir <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember>, veya bir <xref:System.CodeDom.CodeSnippetCompileUnit>. Ancak, kod parçacıkları diğer diller için otomatik olarak CodeDOM tarafından tercüme edilemez.  
  
 CodeDOM türlerinin her biri için belgeler için başvuru belgelerine bakın <xref:System.CodeDom> ad alanı.  
  
 Belirli bir kod öğesi türünü temsil eden CodeDOM öğesini bulmaya yönelik hızlı bir grafik için bkz: [CodeDOM hızlı başvuru](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).
