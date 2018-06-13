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
# <a name="how-to-create-a-class-using-codedom"></a><span data-ttu-id="9394e-102">Nasıl yapılır: CodeDOM Kullanarak Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9394e-102">How to: Create a Class Using CodeDOM</span></span>
<span data-ttu-id="9394e-103">Aşağıdaki yordamlar nasıl oluşturulacağı ve iki alanları, üç özellik, bir yöntemi, bir oluşturucu ve bir giriş noktası içeren bir sınıf oluşturur CodeDOM grafik derleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9394e-103">The following procedures illustrate how to create and compile a CodeDOM graph that generates a class containing two fields, three properties, a method, a constructor, and an entry point.</span></span>  
  
1.  <span data-ttu-id="9394e-104">CodeDOM kodu bir sınıf için kaynak kodunu oluşturmak için kullanacağı bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9394e-104">Create a console application that will use CodeDOM code to generate the source code for a class.</span></span>  
  
     <span data-ttu-id="9394e-105">Bu örnekte, oluşturma sınıfı adlı `Sample`, ve oluşturulan kod adlı bir sınıf `CodeDOMCreatedClass` SampleCode adlı bir dosyaya.</span><span class="sxs-lookup"><span data-stu-id="9394e-105">In this example, the generating class is named `Sample`, and the generated code is a class named `CodeDOMCreatedClass` in a file named SampleCode.</span></span>  
  
2.  <span data-ttu-id="9394e-106">Oluşturma sınıfı, CodeDOM grafiğini başlatma ve üyeleri, oluşturucusu ve giriş noktası tanımlamak için CodeDOM yöntemleri kullanın (`Main` yöntemi) oluşturulan sınıfın.</span><span class="sxs-lookup"><span data-stu-id="9394e-106">In the generating class, initialize the CodeDOM graph and use CodeDOM methods to define the members, constructor, and entry point (`Main` method) of the generated class.</span></span>  
  
     <span data-ttu-id="9394e-107">Bu örnekte, oluşturulan sınıfın iki alanları, üç özellik, bir oluşturucu, bir yöntem sahip ve bir `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9394e-107">In this example, the generated class has two fields, three properties, a constructor, a method, and a `Main` method.</span></span>  
  
3.  <span data-ttu-id="9394e-108">Oluşturulurken, sınıf, dile özgü kodu sağlayıcısı ve çağrı oluşturma kendi <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> grafikten kodunu oluşturmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="9394e-108">In the generating class, create a language-specific code provider and call its <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code from the graph.</span></span>  
  
4.  <span data-ttu-id="9394e-109">Derleyip kodunu oluşturmak için uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9394e-109">Compile and execute the application to generate the code.</span></span>  
  
     <span data-ttu-id="9394e-110">Bu örnekte oluşturulan kod SampleCode adındaki bir dosyada ' dir.</span><span class="sxs-lookup"><span data-stu-id="9394e-110">In this example, the generated code is in a file named SampleCode.</span></span> <span data-ttu-id="9394e-111">Derleme ve örnek çıktı görmek için bu kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9394e-111">Compile and execute that code to see the sample output.</span></span>  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a><span data-ttu-id="9394e-112">CodeDOM kod yürütecek uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9394e-112">To create the application that will execute the CodeDOM code</span></span>  
  
-   <span data-ttu-id="9394e-113">CodeDOM kodu içeren bir konsol uygulama sınıfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9394e-113">Create a console application class to contain the CodeDOM code.</span></span> <span data-ttu-id="9394e-114">Derleme başvurusu için sınıfında kullanılacak genel alanlar tanımlayın (<xref:System.CodeDom.CodeCompileUnit>) ve sınıfı (<xref:System.CodeDom.CodeTypeDeclaration>), oluşturulan kaynak dosyasının adını belirtin ve bildirme `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9394e-114">Define the global fields that are to be used in the class to reference the assembly (<xref:System.CodeDom.CodeCompileUnit>) and class (<xref:System.CodeDom.CodeTypeDeclaration>), specify the name of the generated source file, and declare the `Main` method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a><span data-ttu-id="9394e-115">CodeDOM grafik başlatmak için</span><span class="sxs-lookup"><span data-stu-id="9394e-115">To initialize the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="9394e-116">Konsol uygulama sınıfı oluşturucusu, derleme ve sınıf başlatmak ve uygun bildirimi CodeDOM grafiğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9394e-116">In the constructor for the console application class, initialize the assembly and class, and add the appropriate declarations to the CodeDOM graph.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a><span data-ttu-id="9394e-117">CodeDOM grafiğe üye eklemek için</span><span class="sxs-lookup"><span data-stu-id="9394e-117">To add members to the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="9394e-118">Alanları CodeDOM grafiğe ekleyerek <xref:System.CodeDom.CodeMemberField> nesneleri <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.</span><span class="sxs-lookup"><span data-stu-id="9394e-118">Add fields to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberField> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
-   <span data-ttu-id="9394e-119">Özellikler CodeDOM grafiğe ekleyerek <xref:System.CodeDom.CodeMemberProperty> nesneleri <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.</span><span class="sxs-lookup"><span data-stu-id="9394e-119">Add properties to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberProperty> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
-   <span data-ttu-id="9394e-120">Bir yöntem CodeDOM grafiğe ekleyerek bir <xref:System.CodeDom.CodeMemberMethod> nesnesine <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.</span><span class="sxs-lookup"><span data-stu-id="9394e-120">Add a method to the CodeDOM graph by adding a <xref:System.CodeDom.CodeMemberMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
-   <span data-ttu-id="9394e-121">Bir oluşturucu CodeDOM grafiğe ekleyerek bir <xref:System.CodeDom.CodeConstructor> nesnesine <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.</span><span class="sxs-lookup"><span data-stu-id="9394e-121">Add a constructor to the CodeDOM graph by adding a <xref:System.CodeDom.CodeConstructor> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
-   <span data-ttu-id="9394e-122">Bir giriş noktası CodeDOM grafiğe ekleyerek bir <xref:System.CodeDom.CodeEntryPointMethod> nesnesine <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.</span><span class="sxs-lookup"><span data-stu-id="9394e-122">Add an entry point to the CodeDOM graph by adding a <xref:System.CodeDom.CodeEntryPointMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a><span data-ttu-id="9394e-123">CodeDOM grafikten kodunu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9394e-123">To generate the code from the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="9394e-124">Kaynak kodu çağırarak CodeDOM grafikten Oluştur <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9394e-124">Generate source code from the CodeDOM graph by calling the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a><span data-ttu-id="9394e-125">Grafiği oluşturmak ve kodunu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9394e-125">To create the graph and generate the code</span></span>  
  
1.  <span data-ttu-id="9394e-126">Önceki adımda oluşturulan yöntemler ekleyen `Main` ilk adımda tanımlanan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9394e-126">Add the methods created in the preceding steps to the `Main` method defined in the first step.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2.  <span data-ttu-id="9394e-127">Derleme ve oluşturma sınıfı yürütün.</span><span class="sxs-lookup"><span data-stu-id="9394e-127">Compile and execute the generating class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9394e-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="9394e-128">Example</span></span>  
 <span data-ttu-id="9394e-129">Aşağıdaki kod örneği yukarıdaki adımları kodundan gösterir.</span><span class="sxs-lookup"><span data-stu-id="9394e-129">The following code example shows the code from the preceding steps.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 <span data-ttu-id="9394e-130">Önceki örnekte derlenmiş ve yürütülen olduğunda aşağıdaki kaynak kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9394e-130">When the preceding example is compiled and executed, it produces the following source code.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 <span data-ttu-id="9394e-131">Oluşturulan kaynak kodunu şu derlenmiş ve yürütülen çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="9394e-131">The generated source code produces the following output when compiled and executed.</span></span>  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9394e-132">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9394e-132">Compiling the Code</span></span>  
  
-   <span data-ttu-id="9394e-133">Bu kod örneği gerektirir `FullTrust` izni Ayarla başarıyla yürütülemedi.</span><span class="sxs-lookup"><span data-stu-id="9394e-133">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9394e-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9394e-134">See Also</span></span>  
 [<span data-ttu-id="9394e-135">CodeDOM'yi Kullanma</span><span class="sxs-lookup"><span data-stu-id="9394e-135">Using the CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 [<span data-ttu-id="9394e-136">CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme</span><span class="sxs-lookup"><span data-stu-id="9394e-136">Generating and Compiling Source Code from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)
