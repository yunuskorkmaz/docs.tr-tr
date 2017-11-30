---
title: "-addmodule (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2652102682de9dff24c66180dde36f33b4b6bbfc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="addmodule-c-compiler-options"></a>/addmodule (C# Derleyici Seçenekleri)
Bu seçenek geçerli derlemeye target: module anahtarıyla oluşturulan bir modül ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Arguments  
 `file`, `file2`  
 Meta veriler içeren bir çıktı dosyası. Dosya bir derleme bildirimi içeremez. Birden fazla dosyayı içeri aktarmak için dosya adları virgül veya noktalı virgül ile ayırın.  
  
## <a name="remarks"></a>Açıklamalar  
 İle eklenen tüm modüller **/addmodule** çalışma zamanında çıktı dosyası ile aynı dizinde olmalıdır. Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz ancak modülü çalışma zamanında uygulama dizininde olması gerekir. Modül uygulama dizininde çalışma zamanında değil alırsa bir <xref:System.TypeLoadException>.  
  
 `file`derleme içeremez. Örneğin, çıktı dosyası oluşturulmuşsa [/target: Module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), ile meta verilerini içe **/addmodule**.  
  
 Çıktı dosyası oluşturulmuşsa bir **/target** dışında seçeneği **/target: Module**, ile meta verilerini içeri aktarılamıyor **/addmodule** ancak ileiçeriaktarılabilir[/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Visual Studio'da Bu derleyici seçeneği kullanılamıyor; bir proje bir modüle başvuru yapamaz. Ayrıca, bu derleyici seçeneği programlı olarak değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Kaynak dosyasını derleme `input.cs` ve meta verileri ekleme `metad1.netmodule` ve `metad2.netmodule` üretmek için `out.exe`:  
  
```console  
csc /addmodule:metad1.netmodule;metad2.netmodule /out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)  
 [Birden çok dosya derlemeleri](../../../framework/app-domains/multifile-assemblies.md)  
 [Nasıl yapılır: birden fazla dosya derleme](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
