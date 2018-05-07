---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d28d0556a662099e4e5e74b22583fc3c8b4c313f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-vbruntime"></a>-vbruntime
Visual Basic çalışma zamanı kitaplığı için veya belirli çalışma zamanı kitaplığı başvurusu olan bir başvuru olmadan derleyici derleme belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Arguments  
 \-  
 Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin.  
  
 \+  
 Visual Basic çalışma zamanı kitaplığı varsayılan başvuru derleyin.  
  
 \*  
 Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin ve Visual Basic Çalışma Zamanı Kitaplığı'ndaki çekirdek işlevselliğini derlemesini ekleme.  
  
 `path`  
 Belirtilen kitaplığı (DLL) başvuru derleyin.  
  
## <a name="remarks"></a>Açıklamalar  
 `-vbruntime` Derleyici seçeneği derleyici Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleme belirtmenize olanak sağlar. Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleme yaparsanız, hatalar veya uyarılar bir Visual Basic çalışma zamanı yardımcı çağrısına oluşturan kodu veya dil yapıları üzerinde kaydedilir. (A *Visual Basic çalışma zamanı yardımcı* anlamsal belirli bir dil yürütmek için çalışma zamanında adlı Microsoft.VisualBasic.dll içinde tanımlanan bir işlev.)  
  
 `-vbruntime+` Seçeneği yoksa oluşur aynı davranışı üreten `-vbruntime` anahtarı belirtilir. Kullanabileceğiniz `-vbruntime+` önceki geçersiz kılmak için seçeneği `-vbruntime` anahtarları.  
  
 Çoğu nesnelerin `My` türü, kullandığınızda kullanılamaz `-vbruntime-` veya `-vbruntime:path` seçenekleri.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Visual Basic çalışma zamanı çekirdek işlevselliğini katıştırma  
 `-vbruntime*` Seçeneği, bir çalışma zamanı kitaplığı başvurusu olmadan derleme olanak tanır. Bunun yerine, Visual Basic Çalışma Zamanı Kitaplığı'ndaki çekirdek işlevselliğini kullanıcı derlemede katıştırılır. Visual Basic çalışma zamanı içermeyen platformlarda uygulamanızı çalıştırıyorsa, bu seçeneği kullanabilirsiniz.  
  
 Aşağıdaki çalışma zamanı üyeleri katıştırılmış:  
  
-   <xref:Microsoft.VisualBasic.CompilerServices.Conversions> sınıfı  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> Yöntemi  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> Yöntemi  
  
-   <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> Yöntemi  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack> sabiti  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr> sabiti  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf> sabiti  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed> sabiti  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf> sabiti  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine> sabiti  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar> sabiti  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString> sabiti  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab> sabiti  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab> sabiti  
  
-   Bazı nesnelerin `My` türü  
  
 Kullanarak derleme yaparsanız `-vbruntime*` seçeneği ve kodunuzu çekirdek işlevselliği ile gömülü olmayan Visual Basic Çalışma Zamanı Kitaplığı'ndan üyesi başvuruyor, derleyici üye kullanılamadığını belirten bir hata döndürür.  
  
## <a name="referencing-a-specified-library"></a>Belirtilen kitaplık başvurma  
 Kullanabileceğiniz `path` özel çalışma zamanı kitaplığı Visual Basic çalışma zamanı kitaplığı varsayılan yerine başvuru derlemek için bağımsız değişken.  
  
 Varsa değeri `path` bağımsız değişkeni bir dll dosyasının tam yoludur, derleyici bu dosyayı çalışma zamanı kitaplığı kullanır. Varsa değeri `path` bağımsız değişkeni bir DLL için tam bir yol değil, Visual Basic derleyici geçerli klasörde tanımlanan DLL ilk arar. Ardından, kullanarak belirttiğiniz yolda arar [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) derleyici seçeneği. Varsa `-sdkpath` derleyici seçeneği kullanılmaz, .NET Framework klasöründe tanımlanan DLL derleyici arar (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir `-vbruntime` özel kitaplığına bir başvuru ile derleme seçeneği.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic çekirdek – Visual Studio 2010 SP1'de yeni derleme modu](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
