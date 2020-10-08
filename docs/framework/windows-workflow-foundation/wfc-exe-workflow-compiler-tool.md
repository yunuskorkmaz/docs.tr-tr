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
# <a name="wfcexe-workflow-command-line-compiler-tool"></a>wfc.exe (Iş akışı komut satırı derleyici aracı)
> [!NOTE]
> Bu malzeme artık kullanılmayan türleri ve ad alanlarını açıklamaktadır.

wfc.exe iş akışı komut satırı derleyici aracı, dosya uzantısı *. xoml* (Kullanımdan kaldırılmış) olan eski iş akışı biçimlendirme dosyaları ile birlikte kullanılabilir.

## <a name="compilation-process"></a>Derleme işlemi

İş akışları derlendiğinde, derleme sürecinin bir parçası olarak aşağıdaki yordamlar gerçekleştirilir:

- İş akışı etkinliklerinin kendileri için ayarlanan kurallara göre doğrulanmasını sağlamak için doğrulama gerçekleştirilir. Doğrulama hataları varsa, derleyici hataların bir listesini döndürür.  
- Derleyiciye girdi olan biçimlendirme tanımından kısmi bir sınıf oluşturulur.  

- Kod, etkinliklerin çalışma zamanı yürütmesiyle ilgili yardım için oluşturulur. Olay abonelikleri oluşturulur ve bu etkinlikler, içerdikleri etkinliklerin yürütülmesi bittiğinde size yardımcı olur.  
- Biçimlendirme dosyasından üretilen kısmi sınıflar ve kod dosyasındaki kısmi sınıflar, .NET Framework C# veya Visual Basic derleyicisine girilir. Bu işlemin çıktısı, WorkflowSample.dll .NET derlemesidir. Bu, iş akışını çalıştırmak için dağıtılabilir.

### <a name="compiler-options"></a>Derleyici seçenekleri

Bu bölümde wfc.exe iş akışı komut satırı derleyicisi seçenekleri gösterilmektedir.

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

## <a name="remarks"></a>Açıklamalar
> [!NOTE]
> Bu malzeme artık kullanılmayan türleri ve ad alanlarını açıklamaktadır.

Yetkili türlerin listesi genellikle *wfc.exe.config* dosyasında tanımlanmıştır. İş akışı derlemesinin doğrulama aşamasında, bir iş akışı kaynak belgesi, veya eşlik kuralları dosyası yetkili türler listesinde bulunmayan .NET Framework türlerine doğrudan başvuruyorsa reddedilir. Yetkili türlerin listesi, her girdinin bir `Assembly` , bir `Namespace` , a `TypeName` ve yetkilendirilmiş bir { `True`&#124;`False` } göstergesini gösterdiği bir XML belgesidir. `AuthorizedType` Listedeki bir girdiye karşılık gelir. Tüm ad alanlarını dahil etmek veya hariç tutmak için kullanılabilecek joker karakter gösterimlerinin kullanılmasına izin verilir. Örneğin, `Type="System.*"` <xref:System> alt ad alanlarında bulunan türler dahil olmak üzere içindeki tüm türleri içerir.
  
Yetkilendirilmiş türlerin listesinin kullanımı, seçeneği tarafından denetlenir <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> `'/checktypes'` .

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
> `Type="System.*"`Tür mevcut olduğunda, derleme için gibi diğer istenmeyen türleri dahil etmek mümkündür `Type="System.Configuration"` . Dikkatli olun ve her birini gözden geçirin. Kısıtlanması gereken herhangi bir tür için, öğesini olarak ayarladığınızdan emin `Authorized` olun `False` .

## <a name="see-also"></a>Ayrıca bkz.

- [AuthorizedType sınıfı](xref:System.Workflow.ComponentModel.Compiler.AuthorizedType)
