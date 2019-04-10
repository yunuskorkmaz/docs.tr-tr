---
title: 'Nasıl yapılır: CodeDOM Kullanarak Sınıf Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code Document Object Model, graphs
- Code Document Object Model, creating classes
- graphing with CodeDOM
- CodeDOM, creating classes
- CodeDOM, graphs
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d431fd472df329dd0a8421483eb36b573dce775
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333177"
---
# <a name="how-to-create-a-class-using-codedom"></a>Nasıl yapılır: CodeDOM Kullanarak Sınıf Oluşturma
Aşağıdaki yordamlar oluşturma ve iki alan, üç özellik, bir yöntem, bir oluşturucu ve bir giriş noktası içeren bir sınıf oluşturur bir CodeDOM grafiği derleme işlemini göstermektedir.  
  
1. CodeDOM kod, bir sınıfın kaynak kodu oluşturmak için kullanacağı bir konsol uygulaması oluşturun.  
  
     Bu örnekte, adlı oluşturma sınıfı `Sample`, ve oluşturulan kodun adlı bir sınıf `CodeDOMCreatedClass` SampleCode adındaki bir dosyaya.  
  
2. Oluşturma sınıfı, CodeDOM grafiğini başlatmak ve üyeleri oluşturucusu ve giriş noktası tanımlamak için CodeDOM yöntemleri kullanın (`Main` yöntemi) oluşturulan sınıfın.  
  
     Bu örnekte, oluşturulan sınıfın sahip iki, üç özellik, bir oluşturucu, bir yöntem ve bir `Main` yöntemi.  
  
3. Oluşturma, sınıf, bir dile özel kod sağlayıcısını oluşturup çağrısı kendi <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> grafikten kodunu oluşturmak için yöntemi.  
  
4. Derleme ve kod oluşturmak için uygulamadan yürütün.  
  
     Bu örnekte, oluşturulan kod SampleCode adındaki bir dosyada ' dir. Derlemek ve örnek çıktıyı görmek için bu kodu yürütün.  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a>CodeDOM kod yürüten bir uygulama oluşturmak için  
  
-   CodeDOM kod içeren bir konsol uygulama sınıfı oluşturun. Derlemeye başvuru sınıfında kullanılacak genel alanlar tanımlayın (<xref:System.CodeDom.CodeCompileUnit>) ve sınıf (<xref:System.CodeDom.CodeTypeDeclaration>), oluşturulan kaynak dosyasının adını belirtin ve bildirmek `Main` yöntemi.  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a>CodeDOM grafiği başlatmak için  
  
-   Konsol uygulama sınıfı için oluşturucu, derleme ve sınıf başlatın ve uygun bildirimleri için CodeDOM grafiğini ekleyin.  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a>CodeDOM grafik üyeleri eklemek için  
  
-   Alanlar için CodeDOM grafiğini ekleyerek <xref:System.CodeDom.CodeMemberField> nesneleri için <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
-   Özellikler için CodeDOM grafiğini ekleyerek <xref:System.CodeDom.CodeMemberProperty> nesneleri için <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
-   Bir yöntem için CodeDOM grafiğini ekleyerek bir <xref:System.CodeDom.CodeMemberMethod> nesnesini <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
-   Bir oluşturucu için CodeDOM grafiğini ekleyerek bir <xref:System.CodeDom.CodeConstructor> nesnesini <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
-   Bir giriş noktası için CodeDOM grafiğini ekleyerek bir <xref:System.CodeDom.CodeEntryPointMethod> nesnesini <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a>CodeDOM grafiği kodunu oluşturmak için  
  
-   Kaynak kodu çağırarak CodeDOM grafiği oluşturun <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> yöntemi.  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a>Bir grafik oluşturun ve kod oluşturmak için  
  
1. İçin önceki adımlarda oluşturulan yöntemler `Main` ilk adımda tanımlanan yöntemi.  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. Derleme ve oluşturma sınıfı yürütün.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği önceki adımlarda kodu gösterir.  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 Yukarıdaki örnekte derlenmiş ve yürütülen olduğunda, aşağıdaki kaynak kodunu üretir.  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 Oluşturulan kaynak kodu aşağıdaki derlemenizi ve yürütmenizi, çıktıyı üretir.  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu kod örneği gerektirir `FullTrust` izin kümesinin başarıyla yürütülemedi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CodeDOM'yi Kullanma](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)
- [CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)
