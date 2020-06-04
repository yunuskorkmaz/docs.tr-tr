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
ms.openlocfilehash: 31b719fb7e43cdd6ac44424b359999410dd608a5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403050"
---
# <a name="-vbruntime"></a>-vbruntime
Derleyicinin Visual Basic çalışma zamanı kitaplığına bir başvuru olmadan veya belirli bir çalışma zamanı kitaplığı başvurusuyla derlenmesi gerektiğini belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
 \-  
 Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin.  
  
 \+  
 Varsayılan Visual Basic çalışma zamanı kitaplığı başvurusuyla derleyin.  
  
 \*  
 Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin ve temel işlevselliği Visual Basic çalışma zamanı kitaplığından derlemeye ekleyin.  
  
 `path`  
 Belirtilen kitaplığa (DLL) bir başvuru ile derleyin.  
  
## <a name="remarks"></a>Açıklamalar  
 `-vbruntime`Derleyici seçeneği, derleyicinin Visual Basic çalışma zamanı kitaplığına bir başvuru olmadan derlenmesi gerektiğini belirtmenize olanak sağlar. Visual Basic çalışma zamanı kitaplığına başvuru olmadan derlerseniz, hatalar veya uyarılar bir Visual Basic çalışma zamanı Yardımcısı çağrısı üreten kod veya dil yapılarında günlüğe kaydedilir. ( *Visual Basic çalışma zamanı Yardımcısı* , belirli bir dil anlam yürütmesi yürütmek için çalışma zamanında çağrılan Microsoft. VisualBasic. dll ' de tanımlanan bir işlevdir.)  
  
 `-vbruntime+`Seçeneği, anahtar belirtilmediğinde oluşan aynı davranışı üretir `-vbruntime` . Daha `-vbruntime+` önceki anahtarları geçersiz kılmak için seçeneğini kullanabilirsiniz `-vbruntime` .  
  
 `My`Veya seçeneklerini kullandığınızda, türün çoğu nesne kullanılamaz `-vbruntime-` `-vbruntime:path` .  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Visual Basic çalışma zamanı temel işlevlerini katıştırma  
 `-vbruntime*`Seçeneği, bir çalışma zamanı kitaplığı başvurusu olmadan derlemenize olanak sağlar. Bunun yerine, Visual Basic çalışma zamanı kitaplığındaki çekirdek işlevsellik Kullanıcı derlemesine katıştırılır. Uygulamanız Visual Basic çalışma zamanı içermeyen platformlarda çalışıyorsa, bu seçeneği kullanabilirsiniz.  
  
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
  
- Türün bazı nesneleri `My`  
  
 Seçeneğini kullanarak derlerseniz `-vbruntime*` ve kodunuz çekirdek işlevlerle gömülü olmayan Visual Basic çalışma zamanı kitaplığından bir üyeye başvuruyorsa, derleyici üyenin kullanılamaz olduğunu belirten bir hata döndürür.  
  
## <a name="referencing-a-specified-library"></a>Belirtilen bir kitaplığa başvurma  
 `path`Varsayılan Visual Basic çalışma zamanı kitaplığı yerine özel bir çalışma zamanı kitaplığı başvurusuyla derlemek için bağımsız değişkenini kullanabilirsiniz.  
  
 `path`Bağımsız değişkenin değeri BIR DLL 'nin tam yolu ise, derleyici çalışma zamanı kitaplığı olarak bu dosyayı kullanacaktır. `path`Bağımsız değişkenin değeri BIR DLL 'ye tam yol değilse, Visual Basic derleyici önce geçerli klasörde tanımlanan dll 'yi arar. Daha sonra [-SdkPath](sdkpath.md) derleyici seçeneğini kullanarak belirttiğiniz yolda arama yapılır. `-sdkpath`Derleyici seçeneği kullanılmazsa, derleyici .NET Framework klasöründe () tanımlanan dll 'yi arar `%systemroot%\Microsoft.NET\Framework\versionNumber` .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `-vbruntime` özel bir kitaplığa yönelik bir başvuruya sahip derleme için seçeneğinin nasıl kullanılacağını gösterir.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Core – Visual Studio 2010 SP1 'de yeni derleme modu](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Visual Basic komut satırı derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [-sdkpath](sdkpath.md)
