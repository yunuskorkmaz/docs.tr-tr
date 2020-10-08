---
title: Wfc.exe (Iş akışı komut satırı derleyici aracı)
description: Iş akışı komut satırı derleyici aracını wfc.exe anlayın.
ms.date: 10/10/2020
helpviewer_keywords:
- wfc [Workflow]
- compiler tool
- wfc.exe
- Workflow, compilation
- Workflow, XOML files
- Workflow, wcf
ms.openlocfilehash: cf89962014584adf098118044b063b38b29160b7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844605"
---
# <a name="wfcexe-workflow-command-line-compiler-tool"></a><span data-ttu-id="f471b-103">wfc.exe (Iş akışı komut satırı derleyici aracı)</span><span class="sxs-lookup"><span data-stu-id="f471b-103">wfc.exe (Workflow Command-line Compiler Tool)</span></span>
> [!NOTE]
> <span data-ttu-id="f471b-104">Bu malzeme artık kullanılmayan türleri ve ad alanlarını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="f471b-104">This material discusses types and namespaces that are obsolete.</span></span>

<span data-ttu-id="f471b-105">wfc.exe iş akışı komut satırı derleyici aracı, dosya uzantısı *. xoml* (Kullanımdan kaldırılmış) olan eski iş akışı biçimlendirme dosyaları ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f471b-105">The wfc.exe workflow command-line compiler tool works with old workflow markup files that have the file extension *.xoml* (obsoleted).</span></span>

## <a name="compilation-process"></a><span data-ttu-id="f471b-106">Derleme işlemi</span><span class="sxs-lookup"><span data-stu-id="f471b-106">Compilation process</span></span>

<span data-ttu-id="f471b-107">İş akışları derlendiğinde, derleme sürecinin bir parçası olarak aşağıdaki yordamlar gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="f471b-107">When workflows are compiled, the following procedures are performed as part of the compilation process:</span></span>

- <span data-ttu-id="f471b-108">İş akışı etkinliklerinin kendileri için ayarlanan kurallara göre doğrulanmasını sağlamak için doğrulama gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f471b-108">Validation is performed to ensure that the workflow activities validate based on the rules that the activities have set for themselves.</span></span> <span data-ttu-id="f471b-109">Doğrulama hataları varsa, derleyici hataların bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f471b-109">If there are validation errors, the compiler returns a list of the errors.</span></span>  
- <span data-ttu-id="f471b-110">Derleyiciye girdi olan biçimlendirme tanımından kısmi bir sınıf oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f471b-110">A partial class is generated from the markup definition that is input into the compiler.</span></span>  

- <span data-ttu-id="f471b-111">Kod, etkinliklerin çalışma zamanı yürütmesiyle ilgili yardım için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f471b-111">Code is generated to help with the run-time execution of the activities.</span></span> <span data-ttu-id="f471b-112">Olay abonelikleri oluşturulur ve bu etkinlikler, içerdikleri etkinliklerin yürütülmesi bittiğinde size yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="f471b-112">Event subscriptions are generated, which help activities know when the activities they contain are finished executing.</span></span>  
- <span data-ttu-id="f471b-113">Biçimlendirme dosyasından üretilen kısmi sınıflar ve kod dosyasındaki kısmi sınıflar, .NET Framework C# veya Visual Basic derleyicisine girilir.</span><span class="sxs-lookup"><span data-stu-id="f471b-113">The partial classes generated from the markup file and the partial classes from the code file are entered into the .NET Framework C# or Visual Basic compiler.</span></span> <span data-ttu-id="f471b-114">Bu işlemin çıktısı, WorkflowSample.dll .NET derlemesidir.</span><span class="sxs-lookup"><span data-stu-id="f471b-114">The output of this process is the .NET assembly, WorkflowSample.dll.</span></span> <span data-ttu-id="f471b-115">Bu, iş akışını çalıştırmak için dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="f471b-115">This can be deployed to run the workflow.</span></span>

### <a name="compiler-options"></a><span data-ttu-id="f471b-116">Derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="f471b-116">Compiler options</span></span>

<span data-ttu-id="f471b-117">Bu bölümde wfc.exe iş akışı komut satırı derleyicisi seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f471b-117">This section shows the options for the wfc.exe workflow command-line compiler.</span></span>

```output
    Microsoft (R) Windows Workflow Compiler version 3.0.0.0
    Copyright (C) Microsoft Corporation 2005. All rights reserved.

                      Windows Workflow Compiler Options

    wfc.exe <Xoml file list> /target:assembly [<vb/cs file list>] [/language:...]
            [/out:...] [/reference:...] [/library:...] [/debug...] [/nocode...]
             [/checktypes...] [/resource:<resource info>]

                            - OUTPUT FILE -
    /out:<file>             Output file name
    /target:assembly        Build a Windows Workflow assembly (default).
                            Short form: /t:assembly
    /target:exe             Build a Windows Workflow application.
                            Short form: /t:exe
    /delaysign[+|-]         Delay-sign the assembly using only the public portion
                            of the strong name key.
    /keyfile:<file>         Specifies a strong name key file.
    /keycontainer:<string>  Specifies a strong name key container.

                            - INPUT FILES -
    <Xoml file list>        Xoml source file name(s).
    <vb/cs file list>       Code-beside file name(s).
    /reference:<file list>  Reference metadata from the specified assembly file(s).
                            Short form is '/r:'.
    /library:<path list>    Set of directories where to lookup for the references.
                            Short form is '/lib:'.
    /resource:<resinfo>     Embed the specified resource. Short form is '/res:'.
                            resinfo format is <file>[,<name>[,public|private]].

    Rules and freeform layout files must be embedded as assembly resources.
    The resource name is constructed by using the namespace and type name
    of the activity. For example, an activity named "MyActivity" in namespace
    "WFProject" would require resource names "WFProject.MyActivity.rules"
    and/or "WFProject.MyActivity.layout".

                            - CODE GENERATION -
    /debug[+|-]             Emit full debugging information. The default is '+'.
    /nocode[+|-]            Disallow code-beside model.
                            The default is '-'. Short form is '/nc:'.
    /checktypes[+|-]        Check for permitted types in wfc.exe.config file.
                            The default is '-'. Short form is '/ct:'.

                            - LANGUAGE -
    /language:[cs|vb]       The language to use for the generated class.
                            The default is 'CS' (C#). Short form is '/l:'.
    /rootnamespace:<string> Specifies the root Namespace for all type declarations.
                            Valid only for 'VB' (Visual Basic) language.
                            Short form is '/rns:'.

                            - MISCELLANEOUS -
    /help                   Display this usage message. Short form is '/?'.
    /nologo                 Suppress compiler copyright message. Short form is '/n'.

    /nowarn                 Ignore compiler warnings. Short form is '/w'.
```

## <a name="remarks"></a><span data-ttu-id="f471b-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f471b-118">Remarks</span></span>
> [!NOTE]
> <span data-ttu-id="f471b-119">Bu malzeme artık kullanılmayan türleri ve ad alanlarını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="f471b-119">This material discusses types and namespaces that are obsolete.</span></span>

<span data-ttu-id="f471b-120">Yetkili türlerin listesi genellikle *wfc.exe.config* dosyasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f471b-120">A list of authorized types is usually defined in the *wfc.exe.config* file.</span></span> <span data-ttu-id="f471b-121">İş akışı derlemesinin doğrulama aşamasında, bir iş akışı kaynak belgesi, veya eşlik kuralları dosyası yetkili türler listesinde bulunmayan .NET Framework türlerine doğrudan başvuruyorsa reddedilir.</span><span class="sxs-lookup"><span data-stu-id="f471b-121">During the validation phase of workflow compilation, a workflow source document is rejected if it or the companion rules file directly references any .NET Framework types not present in a list of authorized types.</span></span> <span data-ttu-id="f471b-122">Yetkili türlerin listesi, her girdinin bir `Assembly` , bir `Namespace` , a `TypeName` ve yetkilendirilmiş bir { `True`&#124;`False` } göstergesini gösterdiği bir XML belgesidir.</span><span class="sxs-lookup"><span data-stu-id="f471b-122">The list of authorized types is an XML document where each entry indicates an `Assembly`, a `Namespace`, a `TypeName`, and an Authorized {`True`&#124;`False`} indicator.</span></span> <span data-ttu-id="f471b-123">`AuthorizedType` Listedeki bir girdiye karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f471b-123">`AuthorizedType` corresponds to an entry in the list.</span></span> <span data-ttu-id="f471b-124">Tüm ad alanlarını dahil etmek veya hariç tutmak için kullanılabilecek joker karakter gösterimlerinin kullanılmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="f471b-124">Wildcard character designations, which can be used to include or exclude complete namespaces, are allowed.</span></span> <span data-ttu-id="f471b-125">Örneğin, `Type="System.*"` <xref:System> alt ad alanlarında bulunan türler dahil olmak üzere içindeki tüm türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f471b-125">For example, `Type="System.*"` includes all types in <xref:System>, including types contained in child namespaces.</span></span>
  
<span data-ttu-id="f471b-126">Yetkilendirilmiş türlerin listesinin kullanımı, seçeneği tarafından denetlenir <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> `'/checktypes'` .</span><span class="sxs-lookup"><span data-stu-id="f471b-126">The use of a list of authorized types is controlled by the <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> option `'/checktypes'`.</span></span>

```xml  
<configuration>  
  <System.Workflow.ComponentModel.WorkflowCompiler>
    <authorizedTypes>
      <targetFx version="v4.0">
        ...
        <authorizedType Assembly="System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" Namespace="System*" TypeName="*" Authorized="True"/>
        ...
      </targetFx>
    </authorizedTypes>
  </System.Workflow.ComponentModel.WorkflowCompiler>  
</configuration>  
```

> [!WARNING]
> <span data-ttu-id="f471b-127">`Type="System.*"`Tür mevcut olduğunda, derleme için gibi diğer istenmeyen türleri dahil etmek mümkündür `Type="System.Configuration"` .</span><span class="sxs-lookup"><span data-stu-id="f471b-127">When `Type="System.*"` type is present, it's possible to include other unintended types, such as `Type="System.Configuration"`, for compilation.</span></span> <span data-ttu-id="f471b-128">Dikkatli olun ve her birini gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="f471b-128">You should be cautious and review each one.</span></span> <span data-ttu-id="f471b-129">Kısıtlanması gereken herhangi bir tür için, öğesini olarak ayarladığınızdan emin `Authorized` olun `False` .</span><span class="sxs-lookup"><span data-stu-id="f471b-129">For any type that should be restricted, be sure to set `Authorized` to `False`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f471b-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f471b-130">See also</span></span>

- [<span data-ttu-id="f471b-131">AuthorizedType sınıfı</span><span class="sxs-lookup"><span data-stu-id="f471b-131">AuthorizedType class</span></span>](xref:System.Workflow.ComponentModel.Compiler.AuthorizedType)
