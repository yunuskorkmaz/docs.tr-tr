---
title: 'Nasıl yapılır: CodeDOM kullanarak sınıf oluşturma'
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
ms.openlocfilehash: 78c50b3813ebb0bb65955e411eb84e4cd9e0a001
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54581962"
---
# <a name="how-to-create-a-class-using-codedom"></a><span data-ttu-id="32a95-102">Nasıl yapılır: CodeDOM kullanarak sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="32a95-102">How to: Create a Class Using CodeDOM</span></span>
<span data-ttu-id="32a95-103">Aşağıdaki yordamlar oluşturma ve iki alan, üç özellik, bir yöntem, bir oluşturucu ve bir giriş noktası içeren bir sınıf oluşturur bir CodeDOM grafiği derleme işlemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="32a95-103">The following procedures illustrate how to create and compile a CodeDOM graph that generates a class containing two fields, three properties, a method, a constructor, and an entry point.</span></span>  
  
1.  <span data-ttu-id="32a95-104">CodeDOM kod, bir sınıfın kaynak kodu oluşturmak için kullanacağı bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="32a95-104">Create a console application that will use CodeDOM code to generate the source code for a class.</span></span>  
  
     <span data-ttu-id="32a95-105">Bu örnekte, adlı oluşturma sınıfı `Sample`, ve oluşturulan kodun adlı bir sınıf `CodeDOMCreatedClass` SampleCode adındaki bir dosyaya.</span><span class="sxs-lookup"><span data-stu-id="32a95-105">In this example, the generating class is named `Sample`, and the generated code is a class named `CodeDOMCreatedClass` in a file named SampleCode.</span></span>  
  
2.  <span data-ttu-id="32a95-106">Oluşturma sınıfı, CodeDOM grafiğini başlatmak ve üyeleri oluşturucusu ve giriş noktası tanımlamak için CodeDOM yöntemleri kullanın (`Main` yöntemi) oluşturulan sınıfın.</span><span class="sxs-lookup"><span data-stu-id="32a95-106">In the generating class, initialize the CodeDOM graph and use CodeDOM methods to define the members, constructor, and entry point (`Main` method) of the generated class.</span></span>  
  
     <span data-ttu-id="32a95-107">Bu örnekte, oluşturulan sınıfın sahip iki, üç özellik, bir oluşturucu, bir yöntem ve bir `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32a95-107">In this example, the generated class has two fields, three properties, a constructor, a method, and a `Main` method.</span></span>  
  
3.  <span data-ttu-id="32a95-108">Oluşturma, sınıf, bir dile özel kod sağlayıcısını oluşturup çağrısı kendi <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> grafikten kodunu oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32a95-108">In the generating class, create a language-specific code provider and call its <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code from the graph.</span></span>  
  
4.  <span data-ttu-id="32a95-109">Derleme ve kod oluşturmak için uygulamadan yürütün.</span><span class="sxs-lookup"><span data-stu-id="32a95-109">Compile and execute the application to generate the code.</span></span>  
  
     <span data-ttu-id="32a95-110">Bu örnekte, oluşturulan kod SampleCode adındaki bir dosyada ' dir.</span><span class="sxs-lookup"><span data-stu-id="32a95-110">In this example, the generated code is in a file named SampleCode.</span></span> <span data-ttu-id="32a95-111">Derlemek ve örnek çıktıyı görmek için bu kodu yürütün.</span><span class="sxs-lookup"><span data-stu-id="32a95-111">Compile and execute that code to see the sample output.</span></span>  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a><span data-ttu-id="32a95-112">CodeDOM kod yürüten bir uygulama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="32a95-112">To create the application that will execute the CodeDOM code</span></span>  
  
-   <span data-ttu-id="32a95-113">CodeDOM kod içeren bir konsol uygulama sınıfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="32a95-113">Create a console application class to contain the CodeDOM code.</span></span> <span data-ttu-id="32a95-114">Derlemeye başvuru sınıfında kullanılacak genel alanlar tanımlayın (<xref:System.CodeDom.CodeCompileUnit>) ve sınıf (<xref:System.CodeDom.CodeTypeDeclaration>), oluşturulan kaynak dosyasının adını belirtin ve bildirmek `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32a95-114">Define the global fields that are to be used in the class to reference the assembly (<xref:System.CodeDom.CodeCompileUnit>) and class (<xref:System.CodeDom.CodeTypeDeclaration>), specify the name of the generated source file, and declare the `Main` method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a><span data-ttu-id="32a95-115">CodeDOM grafiği başlatmak için</span><span class="sxs-lookup"><span data-stu-id="32a95-115">To initialize the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="32a95-116">Konsol uygulama sınıfı için oluşturucu, derleme ve sınıf başlatın ve uygun bildirimleri için CodeDOM grafiğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="32a95-116">In the constructor for the console application class, initialize the assembly and class, and add the appropriate declarations to the CodeDOM graph.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a><span data-ttu-id="32a95-117">CodeDOM grafik üyeleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="32a95-117">To add members to the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="32a95-118">Alanlar için CodeDOM grafiğini ekleyerek <xref:System.CodeDom.CodeMemberField> nesneleri için <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.</span><span class="sxs-lookup"><span data-stu-id="32a95-118">Add fields to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberField> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
-   <span data-ttu-id="32a95-119">Özellikler için CodeDOM grafiğini ekleyerek <xref:System.CodeDom.CodeMemberProperty> nesneleri için <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.</span><span class="sxs-lookup"><span data-stu-id="32a95-119">Add properties to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberProperty> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
-   <span data-ttu-id="32a95-120">Bir yöntem için CodeDOM grafiğini ekleyerek bir <xref:System.CodeDom.CodeMemberMethod> nesnesini <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.</span><span class="sxs-lookup"><span data-stu-id="32a95-120">Add a method to the CodeDOM graph by adding a <xref:System.CodeDom.CodeMemberMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
-   <span data-ttu-id="32a95-121">Bir oluşturucu için CodeDOM grafiğini ekleyerek bir <xref:System.CodeDom.CodeConstructor> nesnesini <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.</span><span class="sxs-lookup"><span data-stu-id="32a95-121">Add a constructor to the CodeDOM graph by adding a <xref:System.CodeDom.CodeConstructor> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
-   <span data-ttu-id="32a95-122">Bir giriş noktası için CodeDOM grafiğini ekleyerek bir <xref:System.CodeDom.CodeEntryPointMethod> nesnesini <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> sınıfın özelliği.</span><span class="sxs-lookup"><span data-stu-id="32a95-122">Add an entry point to the CodeDOM graph by adding a <xref:System.CodeDom.CodeEntryPointMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a><span data-ttu-id="32a95-123">CodeDOM grafiği kodunu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="32a95-123">To generate the code from the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="32a95-124">Kaynak kodu çağırarak CodeDOM grafiği oluşturun <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32a95-124">Generate source code from the CodeDOM graph by calling the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a><span data-ttu-id="32a95-125">Bir grafik oluşturun ve kod oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="32a95-125">To create the graph and generate the code</span></span>  
  
1.  <span data-ttu-id="32a95-126">İçin önceki adımlarda oluşturulan yöntemler `Main` ilk adımda tanımlanan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32a95-126">Add the methods created in the preceding steps to the `Main` method defined in the first step.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2.  <span data-ttu-id="32a95-127">Derleme ve oluşturma sınıfı yürütün.</span><span class="sxs-lookup"><span data-stu-id="32a95-127">Compile and execute the generating class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32a95-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="32a95-128">Example</span></span>  
 <span data-ttu-id="32a95-129">Aşağıdaki kod örneği önceki adımlarda kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="32a95-129">The following code example shows the code from the preceding steps.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 <span data-ttu-id="32a95-130">Yukarıdaki örnekte derlenmiş ve yürütülen olduğunda, aşağıdaki kaynak kodunu üretir.</span><span class="sxs-lookup"><span data-stu-id="32a95-130">When the preceding example is compiled and executed, it produces the following source code.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 <span data-ttu-id="32a95-131">Oluşturulan kaynak kodu aşağıdaki derlemenizi ve yürütmenizi, çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="32a95-131">The generated source code produces the following output when compiled and executed.</span></span>  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="32a95-132">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="32a95-132">Compiling the Code</span></span>  
  
-   <span data-ttu-id="32a95-133">Bu kod örneği gerektirir `FullTrust` izin kümesinin başarıyla yürütülemedi.</span><span class="sxs-lookup"><span data-stu-id="32a95-133">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a95-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32a95-134">See also</span></span>
- [<span data-ttu-id="32a95-135">CodeDOM'yi Kullanma</span><span class="sxs-lookup"><span data-stu-id="32a95-135">Using the CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)
- [<span data-ttu-id="32a95-136">CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme</span><span class="sxs-lookup"><span data-stu-id="32a95-136">Generating and Compiling Source Code from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)
