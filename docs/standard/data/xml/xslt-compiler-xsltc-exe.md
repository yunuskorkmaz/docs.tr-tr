---
title: XSLT Derleyicisi (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a0c34eebda789f6561195c89e2660ae77603dc0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923292"
---
# <a name="xslt-compiler-xsltcexe"></a>XSLT Derleyicisi (xsltc.exe)
XSLT derleyicisi (xsltc. exe) XSLT stil sayfalarını derler ve bir derleme oluşturur. Derlenmiş stil sayfası daha sonra doğrudan <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemine geçirilebilir. Xsltc. exe ile imzalı derlemeler oluşturamazsınız.  
  
 Xsltc. exe aracı, Visual Studio 'Ya dahildir. Daha fazla bilgi için bkz. [Visual Studio İndirmeleri](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a>Bağımsız Değişken  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`sourceFile`|Stil sayfasının adını belirtir. Stil sayfası yerel bir dosya olmalıdır veya intranette bulunmalıdır.|  
  
## <a name="options"></a>Seçenekler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/c[lass]:``name`|Aşağıdaki stil sayfası için sınıfın adını belirtir. Sınıf adı tam olarak nitelenmiş olabilir.<br /><br /> Sınıf adı varsayılan olarak stil sayfasının adıdır. Örneğin, Customers. xsl stil sayfası derlenmişse, varsayılan sınıf adı müşteriler olur.|  
|`/debug[`+&#124;-`]`|Hata ayıklama bilgilerinin oluşturulup oluşturulmayacağını belirtir.<br /><br /> `+` Veya`/debug`belirtildiğinde, derleyicinin hata ayıklama bilgileri oluşturmasına ve bir program veritabanı (pdb) dosyasına yerleştirmesine neden olur. Oluşturulan pdb dosyasının adı. pdb 'dir `assemblyName`.<br /><br /> Belirtmiyorsanız geçerli olan öğesini belirtme `-` ,hiçbirhataayıklamabilgisininoluşturulmasınanedenolmaz.`/debug` Bir perakende derlemesi oluşturulur. **Not:**  Hata ayıklama modunda derleme, XSLT performansını önemli ölçüde etkileyebilir.|  
|`/help`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`/nologo`|Derleyicinin telif hakkı iletisinin görüntülenmesini önler.|  
|`/platform:``string`|Derlemenin çalıştırılabilen platformları belirtir. Geçerli platform değerlerini aşağıda açıklanmıştır:<br /><br /> `x86`derlemenizi 32 bit, x86 uyumlu ortak dil çalışma zamanı tarafından çalıştırılacak şekilde derler<br /><br /> `x64`, derlemenizi AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayarda 64 bitlik ortak dil çalışma zamanı tarafından çalıştırılacak şekilde derler.<br /><br /> Itanium, derlemenizi Itanium işlemcisine sahip bir bilgisayarda 64 bitlik ortak dil çalışma zamanı tarafından çalıştırılacak şekilde derler.<br /><br /> `anycpu`derlemenizi herhangi bir platformda çalışacak şekilde derler. Bu varsayılandır.|  
|`/out:``assemblyName`|Çıktı olan derlemenin adını belirtir. Birden çok stil sayfası varsa, derleme adı varsayılan olarak ana stil sayfasının adı veya ilk stil sayfası olur.<br /><br /> Stil sayfası betikler içeriyorsa, betikler ayrı bir derlemeye kaydedilir. Betik derleme adları ana derleme adından oluşturulur. Örneğin, derleme adınız için CustOrders. dll ' yi belirttiyseniz, ilk betik derlemesi CustOrders_Script1. dll olarak adlandırılır.|  
|`/settings:``document+-, script+-, DTD+-,`|Stil sayfasında işlevlere, `document()` XSLT betiğine veya belge türü tanımına (DTD) izin verilip verilmeyeceğini belirtir.<br /><br /> Varsayılan davranış DTD, `document()` işlev ve komut dosyası desteğini devre dışı bırakır.|  
|`@``file`|Derleyici seçeneklerini içeren bir dosya belirtmenizi sağlar.|  
|`?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 XSLT çözümleri, birden çok stil sayfası modülünden oluşabilir. Xsltc. exe aracı, stil sayfalarından derleme oluşturur. Daha sonra derlemeler <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemine geçirilebilir. Bu, bazı XSLT dağıtım senaryolarında performans maliyetlerinin azaltılmasına yardımcı olabilir.  
  
> [!NOTE]
> Derlenen derlemeyi uygulamanıza başvuru olarak da dahil etmeniz gerekir.  
  
 Xsltc. exe aracı,`/class:`Sınıf (*ad*) veya derleme (`/out:`*AssemblyName*) adlarını doğrulamaz. Adlar geçerli değilse, ortak dil çalışma zamanı tarafından hatalar oluşturulur.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, stil sayfasını derler ve booksort. dll adlı bir derleme oluşturur.  
  
```  
xsltc booksort.xsl  
```  
  
 Aşağıdaki komut, stil sayfasını derler ve sırasıyla booksort. dll ve booksort. pdb adlı bir derleme ve PDB dosyası oluşturur.  
  
```  
xsltc booksort.xsl /debug  
```  
  
 Aşağıdaki komut bir msxsl: script öğesi içeren bir stil sayfasını derler ve calc. dll ve calc_Script1. dll adlı iki derleme oluşturur.  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 Aşağıdaki komut DTD işleme ve betik desteğini sunar ve myTest. dll ve myTest_Script1. dll adlı iki derleme oluşturur.  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 Aşağıdaki komut iki stil sayfası modülünü derler ve booksort. dll adlı tek bir derleme oluşturur.  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [Nasıl yapılır: Bütünleştirilmiş kod kullanarak XSLT dönüşümü gerçekleştirme](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
