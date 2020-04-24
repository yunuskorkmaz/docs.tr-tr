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
ms.openlocfilehash: 8c7789c6af7b82ecb40ecd73d09f64aa1da3fd4b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005059"
---
# <a name="-vbruntime"></a>-vbruntime
Derleyicinin Visual Basic çalışma zamanı kitaplığına bir başvuru olmadan veya belirli bir çalışma zamanı kitaplığı başvurusuyla derlenmesi gerektiğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 \-  
 Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin.  
  
 \+  
 Varsayılan Visual Basic çalışma zamanı kitaplığı başvurusuyla derleyin.  
  
 \*  
 Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin ve temel işlevselliği Visual Basic çalışma zamanı kitaplığından derlemeye ekleyin.  
  
 `path`  
 Belirtilen kitaplığa (DLL) bir başvuru ile derleyin.  
  
## <a name="remarks"></a>Açıklamalar  
 `-vbruntime` Derleyici seçeneği, derleyicinin Visual Basic çalışma zamanı kitaplığına bir başvuru olmadan derlenmesi gerektiğini belirtmenize olanak sağlar. Visual Basic çalışma zamanı kitaplığına başvuru olmadan derlerseniz, hatalar veya uyarılar bir Visual Basic çalışma zamanı Yardımcısı çağrısı üreten kod veya dil yapılarında günlüğe kaydedilir. ( *Visual Basic çalışma zamanı Yardımcısı* , belirli bir dil anlam yürütmesi yürütmek için çalışma zamanında çağrılan Microsoft. VisualBasic. dll ' de tanımlanan bir işlevdir.)  
  
 `-vbruntime+` Seçeneği, `-vbruntime` anahtar belirtilmediğinde oluşan aynı davranışı üretir. Daha önceki `-vbruntime` anahtarları geçersiz `-vbruntime+` kılmak için seçeneğini kullanabilirsiniz.  
  
 Veya seçeneklerini kullandığınızda, `My` `-vbruntime:path` türün çoğu nesne `-vbruntime-` kullanılamaz.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Visual Basic çalışma zamanı temel işlevlerini katıştırma  
 Seçeneği `-vbruntime*` , bir çalışma zamanı kitaplığı başvurusu olmadan derlemenize olanak sağlar. Bunun yerine, Visual Basic çalışma zamanı kitaplığındaki çekirdek işlevsellik Kullanıcı derlemesine katıştırılır. Uygulamanız Visual Basic çalışma zamanı içermeyen platformlarda çalışıyorsa, bu seçeneği kullanabilirsiniz.  
  
 Aşağıdaki çalışma zamanı üyeleri katıştırılır:  
  
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions> sınıfı  
  
- <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> yöntemi  
  
- <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> yöntemi  
  
- <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> yöntemi  
  
- <xref:Microsoft.VisualBasic.Constants.vbBack>sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbCr>sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbCrLf>sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbFormFeed>sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbLf>sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbNewLine>sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbNullChar>sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbNullString>sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbTab>sabit  
  
- <xref:Microsoft.VisualBasic.Constants.vbVerticalTab>sabit  
  
- `My` Türün bazı nesneleri  
  
 `-vbruntime*` Seçeneğini kullanarak derlerseniz ve kodunuz çekirdek işlevlerle gömülü olmayan Visual Basic çalışma zamanı kitaplığından bir üyeye başvuruyorsa, derleyici üyenin kullanılamaz olduğunu belirten bir hata döndürür.  
  
## <a name="referencing-a-specified-library"></a>Belirtilen bir kitaplığa başvurma  
 Varsayılan Visual Basic çalışma zamanı `path` kitaplığı yerine özel bir çalışma zamanı kitaplığı başvurusuyla derlemek için bağımsız değişkenini kullanabilirsiniz.  
  
 `path` Bağımsız değişkenin DEĞERI bir dll 'nin tam yolu ise, derleyici çalışma zamanı kitaplığı olarak bu dosyayı kullanacaktır. `path` Bağımsız değişkenin DEĞERI bir dll 'ye tam yol değilse, Visual Basic derleyici önce geçerli KLASÖRDE tanımlanan dll 'yi arar. Daha sonra [-SdkPath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) derleyici seçeneğini kullanarak belirttiğiniz yolda arama yapılır. `-sdkpath` Derleyici seçeneği kullanılmazsa, derleyici .NET Framework klasöründe (`%systemroot%\Microsoft.NET\Framework\versionNumber`) tanımlanan dll 'yi arar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özel bir kitaplığa yönelik bir `-vbruntime` başvuruya sahip derleme için seçeneğinin nasıl kullanılacağını gösterir.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Core – Visual Studio 2010 SP1 'de yeni derleme modu](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
