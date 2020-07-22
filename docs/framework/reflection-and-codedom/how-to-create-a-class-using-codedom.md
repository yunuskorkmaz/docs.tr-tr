---
title: 'Nasıl yapılır: CodeDOM Kullanarak Sınıf Oluşturma'
description: Kod Belge Nesne Modeli (CodeDOM) kullanarak bir sınıfın nasıl oluşturulacağını açıklayan ayrıntılı bir örneğe bakın.
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
ms.openlocfilehash: 3d7151d384402dba6fbb5da8fe54621346251f7b
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865313"
---
# <a name="how-to-create-a-class-using-codedom"></a><span data-ttu-id="d2741-103">Nasıl yapılır: CodeDOM Kullanarak Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2741-103">How to: Create a Class Using CodeDOM</span></span>
<span data-ttu-id="d2741-104">Aşağıdaki yordamlarda, iki alanı, üç özellik, bir yöntemi, oluşturucuyu ve bir giriş noktasını içeren bir sınıf üreten bir CodeDOM grafiği oluşturma ve derleme işlemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d2741-104">The following procedures illustrate how to create and compile a CodeDOM graph that generates a class containing two fields, three properties, a method, a constructor, and an entry point.</span></span>  
  
1. <span data-ttu-id="d2741-105">Bir sınıf için kaynak kodu oluşturmak üzere CodeDOM kodunu kullanacak bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d2741-105">Create a console application that will use CodeDOM code to generate the source code for a class.</span></span>  
  
     <span data-ttu-id="d2741-106">Bu örnekte, üretilen sınıf adlandırılır `Sample` ve oluşturulan kod, `CodeDOMCreatedClass` SampleCode adlı bir dosyada adlı bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="d2741-106">In this example, the generating class is named `Sample`, and the generated code is a class named `CodeDOMCreatedClass` in a file named SampleCode.</span></span>  
  
2. <span data-ttu-id="d2741-107">Oluşturma sınıfında, CodeDOM grafiğini başlatın ve oluşturulan sınıfın üyelerini, oluşturucusunu ve giriş noktasını (yöntemini) tanımlamak için CodeDOM yöntemlerini kullanın `Main` .</span><span class="sxs-lookup"><span data-stu-id="d2741-107">In the generating class, initialize the CodeDOM graph and use CodeDOM methods to define the members, constructor, and entry point (`Main` method) of the generated class.</span></span>  
  
     <span data-ttu-id="d2741-108">Bu örnekte, oluşturulan sınıfın iki alanı, üç özelliği, bir Oluşturucu, bir yöntemi ve `Main` yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="d2741-108">In this example, the generated class has two fields, three properties, a constructor, a method, and a `Main` method.</span></span>  
  
3. <span data-ttu-id="d2741-109">Oluşturma sınıfında, bir dile özgü kod sağlayıcı oluşturun ve bu kodu <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> grafikten kodu oluşturmak için metodunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="d2741-109">In the generating class, create a language-specific code provider and call its <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code from the graph.</span></span>  
  
4. <span data-ttu-id="d2741-110">Kodu oluşturmak için uygulamayı derleyin ve yürütün.</span><span class="sxs-lookup"><span data-stu-id="d2741-110">Compile and execute the application to generate the code.</span></span>  
  
     <span data-ttu-id="d2741-111">Bu örnekte, oluşturulan kod SampleCode adlı bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="d2741-111">In this example, the generated code is in a file named SampleCode.</span></span> <span data-ttu-id="d2741-112">Örnek çıktıyı görmek için kodu derleyin ve yürütün.</span><span class="sxs-lookup"><span data-stu-id="d2741-112">Compile and execute that code to see the sample output.</span></span>  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a><span data-ttu-id="d2741-113">CodeDOM kodunu yürütecek uygulamayı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d2741-113">To create the application that will execute the CodeDOM code</span></span>  
  
- <span data-ttu-id="d2741-114">CodeDOM kodunu içeren bir konsol uygulaması sınıfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d2741-114">Create a console application class to contain the CodeDOM code.</span></span> <span data-ttu-id="d2741-115">Sınıfta () ve sınıfına () başvurmak için kullanılan genel alanları tanımlayın <xref:System.CodeDom.CodeCompileUnit> <xref:System.CodeDom.CodeTypeDeclaration> , oluşturulan kaynak dosyanın adını belirtin ve `Main` yöntemi bildirin.</span><span class="sxs-lookup"><span data-stu-id="d2741-115">Define the global fields that are to be used in the class to reference the assembly (<xref:System.CodeDom.CodeCompileUnit>) and class (<xref:System.CodeDom.CodeTypeDeclaration>), specify the name of the generated source file, and declare the `Main` method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a><span data-ttu-id="d2741-116">CodeDOM grafiğini başlatmak için</span><span class="sxs-lookup"><span data-stu-id="d2741-116">To initialize the CodeDOM graph</span></span>  
  
- <span data-ttu-id="d2741-117">Konsol uygulaması sınıfının oluşturucusunda, derlemeyi ve sınıfını başlatın ve CodeDOM grafiğine uygun bildirimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d2741-117">In the constructor for the console application class, initialize the assembly and class, and add the appropriate declarations to the CodeDOM graph.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a><span data-ttu-id="d2741-118">CodeDOM grafiğine üye eklemek için</span><span class="sxs-lookup"><span data-stu-id="d2741-118">To add members to the CodeDOM graph</span></span>  
  
- <span data-ttu-id="d2741-119">Sınıfının özelliğine nesneler ekleyerek CodeDOM grafiğine alanlar ekleyin <xref:System.CodeDom.CodeMemberField> <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> .</span><span class="sxs-lookup"><span data-stu-id="d2741-119">Add fields to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberField> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
- <span data-ttu-id="d2741-120">Sınıfının özelliğine nesneler ekleyerek CodeDOM grafiğine özellikler ekleyin <xref:System.CodeDom.CodeMemberProperty> <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> .</span><span class="sxs-lookup"><span data-stu-id="d2741-120">Add properties to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberProperty> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
- <span data-ttu-id="d2741-121">Sınıfının özelliğine bir nesne ekleyerek CodeDOM grafiğine bir yöntem ekleyin <xref:System.CodeDom.CodeMemberMethod> <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> .</span><span class="sxs-lookup"><span data-stu-id="d2741-121">Add a method to the CodeDOM graph by adding a <xref:System.CodeDom.CodeMemberMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
- <span data-ttu-id="d2741-122">Sınıfının özelliğine bir nesne ekleyerek CodeDOM grafiğine bir Oluşturucu ekleyin <xref:System.CodeDom.CodeConstructor> <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> .</span><span class="sxs-lookup"><span data-stu-id="d2741-122">Add a constructor to the CodeDOM graph by adding a <xref:System.CodeDom.CodeConstructor> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
- <span data-ttu-id="d2741-123">Sınıfının özelliğine bir nesne ekleyerek CodeDOM grafiğine bir giriş noktası ekleyin <xref:System.CodeDom.CodeEntryPointMethod> <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> .</span><span class="sxs-lookup"><span data-stu-id="d2741-123">Add an entry point to the CodeDOM graph by adding a <xref:System.CodeDom.CodeEntryPointMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a><span data-ttu-id="d2741-124">CodeDOM grafiğinden kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d2741-124">To generate the code from the CodeDOM graph</span></span>  
  
- <span data-ttu-id="d2741-125">Yöntemini çağırarak CodeDOM grafiğinden kaynak kodu oluşturun <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> .</span><span class="sxs-lookup"><span data-stu-id="d2741-125">Generate source code from the CodeDOM graph by calling the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a><span data-ttu-id="d2741-126">Grafiği oluşturmak ve kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d2741-126">To create the graph and generate the code</span></span>  
  
1. <span data-ttu-id="d2741-127">Önceki adımlarda oluşturulan yöntemleri `Main` ilk adımda tanımlanan yönteme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d2741-127">Add the methods created in the preceding steps to the `Main` method defined in the first step.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. <span data-ttu-id="d2741-128">Oluşturulan sınıfı derleyin ve yürütün.</span><span class="sxs-lookup"><span data-stu-id="d2741-128">Compile and execute the generating class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2741-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2741-129">Example</span></span>  
 <span data-ttu-id="d2741-130">Aşağıdaki kod örneği, önceki adımlardan kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2741-130">The following code example shows the code from the preceding steps.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 <span data-ttu-id="d2741-131">Yukarıdaki örnek derlenip yürütüldüğünde, aşağıdaki kaynak kodu üretir.</span><span class="sxs-lookup"><span data-stu-id="d2741-131">When the preceding example is compiled and executed, it produces the following source code.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 <span data-ttu-id="d2741-132">Oluşturulan kaynak kodu derlendiğinde ve yürütüldüğünde aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="d2741-132">The generated source code produces the following output when compiled and executed.</span></span>  
  
```output
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d2741-133">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d2741-133">Compiling the Code</span></span>  
  
- <span data-ttu-id="d2741-134">Bu kod örneği, `FullTrust` izin kümesinin başarıyla yürütülmesine gerek duyar.</span><span class="sxs-lookup"><span data-stu-id="d2741-134">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2741-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2741-135">See also</span></span>

- [<span data-ttu-id="d2741-136">CodeDOM'yi Kullanma</span><span class="sxs-lookup"><span data-stu-id="d2741-136">Using the CodeDOM</span></span>](using-the-codedom.md)
- [<span data-ttu-id="d2741-137">CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme</span><span class="sxs-lookup"><span data-stu-id="d2741-137">Generating and Compiling Source Code from a CodeDOM Graph</span></span>](generating-and-compiling-source-code-from-a-codedom-graph.md)
