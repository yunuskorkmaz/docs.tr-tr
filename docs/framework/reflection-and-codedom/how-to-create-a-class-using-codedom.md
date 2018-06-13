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
ms.openlocfilehash: cf244e796dad0f3817a3c5acd1fcda8eaf189e2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395394"
---
# <a name="how-to-create-a-class-using-codedom"></a>Nasıl yapılır: CodeDOM Kullanarak Sınıf Oluşturma
Aşağıdaki yordamlar nasıl oluşturulacağı ve iki alanları, üç özellik, bir yöntemi, bir oluşturucu ve bir giriş noktası içeren bir sınıf oluşturur CodeDOM grafik derleme gösterilmektedir.  
  
1.  CodeDOM kodu bir sınıf için kaynak kodunu oluşturmak için kullanacağı bir konsol uygulaması oluşturun.  
  
     Bu örnekte, oluşturma sınıfı adlı `Sample`, ve oluşturulan kod adlı bir sınıf `CodeDOMCreatedClass` SampleCode adlı bir dosyaya.  
  
2.  Oluşturma sınıfı, CodeDOM grafiğini başlatma ve üyeleri, oluşturucusu ve giriş noktası tanımlamak için CodeDOM yöntemleri kullanın (`Main` yöntemi) oluşturulan sınıfın.  
  
     Bu örnekte, oluşturulan sınıfın iki alanları, üç özellik, bir oluşturucu, bir yöntem sahip ve bir `Main` yöntemi.  
  
3.  Oluşturulurken, sınıf, dile özgü kodu sağlayıcısı ve çağrı oluşturma kendi <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> grafikten kodunu oluşturmak için yöntem.  
  
4.  Derleyip kodunu oluşturmak için uygulamayı çalıştırın.  
  
     Bu örnekte oluşturulan kod SampleCode adındaki bir dosyada ' dir. Derleme ve örnek çıktı görmek için bu kodu çalıştırın.  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a>CodeDOM kod yürütecek uygulaması oluşturmak için  
  
-   CodeDOM kodu içeren bir konsol uygulama sınıfı oluşturun. Derleme başvurusu için sınıfında kullanılacak genel alanlar tanımlayın (<xref:System.CodeDom.CodeCompileUnit>) ve sınıfı (<xref:System.CodeDom.CodeTypeDeclaration>), oluşturulan kaynak dosyasının adını belirtin ve bildirme `Main` yöntemi.  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a>CodeDOM grafik başlatmak için  
  
-   Konsol uygulama sınıfı oluşturucusu, derleme ve sınıf başlatmak ve uygun bildirimi CodeDOM grafiğe ekleyin.  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a>CodeDOM grafiğe üye eklemek için  
  
-   Alanları CodeDOM grafiğe ekleyerek <xref:System.CodeDom.CodeMemberField> nesneleri <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
-   Özellikler CodeDOM grafiğe ekleyerek <xref:System.CodeDom.CodeMemberProperty> nesneleri <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
-   Bir yöntem CodeDOM grafiğe ekleyerek bir <xref:System.CodeDom.CodeMemberMethod> nesnesine <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
-   Bir oluşturucu CodeDOM grafiğe ekleyerek bir <xref:System.CodeDom.CodeConstructor> nesnesine <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
-   Bir giriş noktası CodeDOM grafiğe ekleyerek bir <xref:System.CodeDom.CodeEntryPointMethod> nesnesine <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a>CodeDOM grafikten kodunu oluşturmak için  
  
-   Kaynak kodu çağırarak CodeDOM grafikten Oluştur <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> yöntemi.  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a>Grafiği oluşturmak ve kodunu oluşturmak için  
  
1.  Önceki adımda oluşturulan yöntemler ekleyen `Main` ilk adımda tanımlanan yöntemi.  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2.  Derleme ve oluşturma sınıfı yürütün.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği yukarıdaki adımları kodundan gösterir.  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 Önceki örnekte derlenmiş ve yürütülen olduğunda aşağıdaki kaynak kodu oluşturur.  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 Oluşturulan kaynak kodunu şu derlenmiş ve yürütülen çıktıyı üretir.  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu kod örneği gerektirir `FullTrust` izni Ayarla başarıyla yürütülemedi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CodeDOM'yi Kullanma](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 [CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)
