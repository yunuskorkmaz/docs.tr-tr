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
ms.openlocfilehash: 56ea692d6e65d94c497fbc9406e03b40648c55a2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663493"
---
# <a name="-vbruntime"></a>-vbruntime
Derleyici, Visual Basic çalışma zamanı kitaplığı veya bir belirli çalışma zamanı kitaplık başvurusu olan bir başvuru olmadan derlemesi gerektiğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Arguments  
 \-  
 Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin.  
  
 \+  
 Varsayılan Visual Basic çalışma zamanı kitaplığı başvurusu ile derleyin.  
  
 \*  
 Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin ve Visual Basic Çalışma Zamanı Kitaplığı'ndan derleme çekirdek işlevselliği ekleme.  
  
 `path`  
 Belirtilen kitaplık (DLL) başvuru ile derleyin.  
  
## <a name="remarks"></a>Açıklamalar  
 `-vbruntime` Derleyici seçeneği derleyici Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derlemesi gerektiğini belirtmenize imkan tanır. Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleme yaparsanız, hatalar veya uyarılar bir Visual Basic çalışma zamanı yardımcı çağrısı oluşturan kodu veya dil yapıları üzerinde günlüğe kaydedilir. (A *Visual Basic çalışma zamanı Yardımcısı* anlam belirli bir dil yürütmek için çalışma zamanında çağrılan Microsoft.VisualBasic.dll içinde tanımlanan bir işlevdir.)  
  
 `-vbruntime+` Seçeneği Hayır ise oluşan aynı davranışı üretir `-vbruntime` anahtarı belirtiliyor. Kullanabileceğiniz `-vbruntime+` önceki geçersiz kılmak için seçeneği `-vbruntime` anahtarlar.  
  
 Çoğu nesnelerin `My` türü, kullandığınızda kullanılamaz `-vbruntime-` veya `-vbruntime:path` seçenekleri.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Visual Basic çalışma zamanı çekirdek işlevselliği ekleme  
 `-vbruntime*` Seçeneği bir çalışma zamanı kitaplığı başvurusu olmadan derleme olanak sağlar. Bunun yerine, Visual Basic Çalışma Zamanı Kitaplığı'ndaki çekirdek işlevselliğini kullanıcı derlemesinde katıştırılır. Visual Basic çalışma zamanı içermeyen platformlarda uygulamanız çalışıyorsa, bu seçeneği kullanabilirsiniz.  
  
 Aşağıdaki çalışma zamanı üyeleri bir parçasıdır:  
  
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions> Sınıfı  
  
- <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> Yöntemi  
  
- <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> Yöntemi  
  
- <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> Yöntemi  
  
- <xref:Microsoft.VisualBasic.Constants.vbBack> Sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbCr> Sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbCrLf> Sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbFormFeed> Sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbLf> Sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbNewLine> Sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbNullChar> Sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbNullString> Sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbTab> Sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbVerticalTab> Sabit  
  
- Bazı nesneler `My` türü  
  
 Kullanarak derleme yaparsanız `-vbruntime*` seçeneği ve kodunuzu çekirdek işlevselliği gömülü Visual Basic Çalışma Zamanı Kitaplığı'ndan bir üye başvuruyor, derleyici üyesi kullanılabilir olmadığını belirten bir hata döndürür.  
  
## <a name="referencing-a-specified-library"></a>Belirtilen kitaplık başvurma  
 Kullanabileceğiniz `path` bir Visual Basic çalışma zamanı kitaplığı varsayılan yerine özel çalışma zamanı kitaplık başvurusu olan derlemek için bağımsız değişken.  
  
 Varsa değerini `path` bağımsız değişkeni bir dll dosyasının tam yolu, derleyici bu dosyayı çalışma zamanı kitaplığı kullanır. Varsa değerini `path` bağımsız değişkeni bir tam bir DLL yolu değil, Visual Basic Derleyicisi geçerli klasörde belirtilen DLL için ilk arama yapar. Ardından kullanılarak belirtilen yolda arar [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) derleyici seçeneği. Varsa `-sdkpath` derleyici seçeneği kullanılmazsa, derleyici, .NET Framework klasöründe tanımlanmış DLL için arama yapar (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `-vbruntime` özel bir kitaplığa bir başvuru ile derlemek için seçeneği.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic çekirdek – Visual Studio 2010 SP1'de yeni derleme modu](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
