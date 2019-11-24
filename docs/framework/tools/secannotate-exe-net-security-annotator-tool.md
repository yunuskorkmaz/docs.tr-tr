---
title: SecAnnotate.exe (.NET Güvenlik Not Ekleyici Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
ms.openlocfilehash: cc57bd01c5626c889b5d94eac1e7358cafa4ab10
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447315"
---
# <a name="secannotateexe-net-security-annotator-tool"></a>SecAnnotate.exe (.NET Güvenlik Not Ekleyici Aracı)
The .NET Security Annotator tool (SecAnnotate.exe) is a command-line application that identifies the `SecurityCritical` and `SecuritySafeCritical` portions of one or more assemblies.  
  
 A Visual Studio extension, [Security Annotator](https://marketplace.visualstudio.com/items?itemName=sheldonb.SecurityAnnotator), provides a graphical user interface to SecAnnotate.exe and enables you to run the tool from Visual Studio.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). For more information, see [Command Prompts](developer-command-prompt-for-vs.md).  
  
 At the command prompt, type the following, where *parameters* are described in the following section, and *assemblies* consist of one or more assembly names separated by blanks:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
SecAnnotate.exe [parameters] [assemblies]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/a`<br /><br /> veya<br /><br /> `/showstatistics`|Analiz edilmekte olan derlemelerde saydamlık kullanımıyla ilgili istatistikleri gösterir.|  
|`/d:` *directory*<br /><br /> veya<br /><br /> `/referencedir:` *directory*|Ek açıklama sırasında bağımlı derlemelerin aranacağı bir dizin belirtir.|  
|`/i`<br /><br /> veya<br /><br /> `/includesignatures`|Ek açıklama raporu dosyasına genişletilmiş imza bilgileri ekler.|  
|`/n`<br /><br /> veya<br /><br /> `/nogac`|Genel derleme belleğinde başvurulan derlemelerin aranmasını bastırır.|  
|`/o:` *output.xml*<br /><br /> veya<br /><br /> `/out:` *output.xml*|Çıktı ek açıklama dosyasını belirtir.|  
|`/p:` *maxpasses*<br /><br /> veya<br /><br /> `/maximumpasses:` *maxpasses*|Yeni ek açıklamaların üretilmesini durdurmadan önce derlemelere yapılacak en fazla ek açıklama sayısını belirtir.|  
|`/q`<br /><br /> veya<br /><br /> `/quiet`|Açıklama ekleyicinin durum iletileri vermediği sessiz modu belirtir; yalnızca hata bilgilerini verir.|  
|`/r:` *assembly*<br /><br /> veya<br /><br /> `/referenceassembly:` *assembly*|Açıklama ekleme sırasında bağımlı derlemeleri çözerken, belirtilen derlemeyi ekler. Başvuru derlemelerine, başvuru yolunda bulunan derlemelere göre öncelik verilir.|  
|`/s:` *rulename*<br /><br /> veya<br /><br /> `/suppressrule:` *rulename*|Belirtilen saydamlık kuralını giriş derlemeleri üzerinde çalıştırmayı bastırır.|  
|`/t`<br /><br /> veya<br /><br /> `/forcetransparent`|Açıklama Ekleyici aracını, herhangi bir saydamlık ek açıklaması olmayan tüm derlemelere tümüyle saydamlarmış gibi davranmaya zorlar.|  
|`/t`:*assembly*<br /><br /> veya<br /><br /> `/forcetransparent`:*assembly*|Derleme düzeyindeki geçerli ek açıklamalarına bakılmaksızın, verilen derlemeyi saydam olmaya zorlar.|  
|||  
|`/v`<br /><br /> veya<br /><br /> `/verify`|Yalnızca bir derlemenin ek açıklamalarının doğru olduğunu doğrular; derleme doğrulamazsa, gerekli tüm ek açıklamaları bulmak için birden çok geçiş yapmayı denemez.|  
|`/x`<br /><br /> veya<br /><br /> `/verbose`|Ek açıklama eklerken ayrıntılı çıktı belirtir.|  
|`/y:` *directory*<br /><br /> veya<br /><br /> `/symbolpath:` *directory*|Açıklama ekleme sırasında simge dosyalarını ararken, belirtilen dizini ekler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Komut satırında belirtilen ve önüne bir at işareti (@) eklenen bir yanıt dosyasında parametreler ve derlemeler de sağlanabilir. Yanıt dosyasındaki her bir satır tek bir parametre veya derleme adı içermelidir.  
  
 For more information about the .NET Security Annotator, see the entry [Using SecAnnotate to Analyze Your Assemblies for Transparency Violations](https://blogs.msdn.microsoft.com/shawnfa/2009/11/18/using-secannotate-to-analyze-your-assemblies-for-transparency-violations-an-example/) in the .NET Security blog.  
  
## <a name="examples"></a>Örnekler
