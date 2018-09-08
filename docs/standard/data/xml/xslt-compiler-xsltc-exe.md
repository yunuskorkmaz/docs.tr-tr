---
title: XSLT derleyicisi (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 470dd0eb37d8081d388ef69b204293f568096a5e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197559"
---
# <a name="xslt-compiler-xsltcexe"></a>XSLT derleyicisi (xsltc.exe)
XSLT derleyicisi (xsltc.exe) XSLT stil sayfalarını derler ve bir derleme oluşturur. Derlenmiş bir stil sayfası sonra doğrudan geçirilebilir <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemi. İmzalı derlemeler xsltc.exe ile oluşturulamıyor.  
  
 Xsltc.exe aracı Visual Studio ile birlikte gelir. Daha fazla bilgi için [Visual Studio indirmeleri](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a>Bağımsız Değişken  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`sourceFile`|Stil sayfası adını belirtir. Stil sayfası, yerel bir dosya olmalıdır veya intranette yer.|  
  
## <a name="options"></a>Seçenekler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/c[lass]:``name`|Aşağıdaki stil sayfası için sınıfın adını belirtir. Sınıf adı, tam olabilir.<br /><br /> Sınıf adı, stil sayfası adını varsayılan olarak. Örneğin, stil sayfası customers.xsl derlenirse, varsayılan sınıf adını Müşteriler ' dir.|  
|`/debug[`+&#124;-`]`|Hata ayıklama bilgilerini oluşturulup oluşturulmayacağını belirtir.<br /><br /> Belirtme `+` veya `/debug`, derleyicinin hata ayıklama bilgileri üret ve program veritabanı (PDB) dosyası içinde yerleştirin. Oluşturulan PDB dosyası adıdır `assemblyName`.pdb.<br /><br /> Belirtme `-`, hangi belirtmezseniz, geçerli olduğu `/debug`, oluşturulacak hata ayıklama bilgisi yok neden olur. Bir perakende derleme oluşturulur. **Not:** hata ayıklama modunda derleme etkileyebilir XSLT performansı önemli ölçüde.|  
|`/help`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`/nologo`|Derleyici telif hakkı iletisini görüntülenmesini bastırır.|  
|`/platform:``string`|Derleme çalıştırılabileceği platformları belirtir. Geçerli platform değerleri açıklar:<br /><br /> `x86` derlemenizi 32-bit, x86 uyumlu ortak dil çalışma zamanı tarafından çalıştırılmak üzere<br /><br /> `x64` derlemenizi 64 bit ortak dil çalışma zamanı tarafından AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayarda çalıştırılması için derler.<br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] derlemenizi 64 bit ortak dil çalışma zamanı tarafından olan bir bilgisayarda çalıştırılması için bir [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] işlemci.<br /><br /> `anycpu` Herhangi bir platform üzerinde çalıştırmasını derlemenizin derler. Bu varsayılandır.|  
|`/out:``assemblyName`|Çıkış derlemesi adını belirtir. Birden çok stil sayfaları varsa ana stil sayfası veya ilk stil sayfası adı için varsayılan derleme adı içerir.<br /><br /> Betikleri stil sayfası içeriyorsa, komut dosyaları için ayrı bir derleme kaydedilir. Komut dosyası derleme adları ana derleme adından oluşturulur. Örneğin, derleme adınız için CustOrders.dll belirttiyseniz, ilk betik derleme CustOrders_Script1.dll olarak adlandırılır.|  
|`/settings:``document+-, script+-, DTD+-,`|İzin verilip verilmeyeceğini belirten `document()` işlevleri, XSLT betik veya belge stil sayfası içinde tür tanımı (DTD'nin).<br /><br /> DTD desteği varsayılan davranışı devre dışı bırakır `document()` işlev ve betik oluşturma.|  
|`@``file`|Derleyici seçenekleri içeren bir dosya belirtmenizi sağlar.|  
|`?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 XSLT çözümleri birden çok stil sayfası modüllerini oluşabilir. Xsltc.exe araç derlemeleri stil sayfası içinden oluşturur. Derlemeleri ardından uygulamasına geçirilebilir <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemi. Bu, bazı XSLT dağıtım senaryolarında performans maliyetleri azaltma yardımcı olabilir.  
  
> [!NOTE]
>  Uygulamanızda bir başvuru olarak derlenmiş derlemenin de dahil etmelisiniz.  
  
 Xsltc.exe araç, sınıf doğrulamaz (`/class:``name`) veya derleme (`/out:``assemblyName`) adları. Adları geçerli değilse, hatalar ortak dil çalışma zamanı tarafından atılır.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, stil sayfası derler ve booksort.dll adlı bir derleme oluşturur.  
  
```  
xsltc booksort.xsl  
```  
  
 Aşağıdaki komut, stil sayfası derler ve bir derleme ve booksort.dll ve booksort.pdb sırasıyla adlı PDB dosyası oluşturur.  
  
```  
xsltc booksort.xsl /debug  
```  
  
 Aşağıdaki komutu bir msxsl: Script öğesi içeriyor ve calc.dll ve calc_Script1.dll adlı iki derlemeler oluşturan bir stil sayfası derler.  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 Aşağıdaki komut, DTD işleme ve komut dosyası desteği sağlar ve myTest.dll ve myTest_Script1.dll adlı iki derleme oluşturur.  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 Aşağıdaki komut, iki stil sayfası modülleri derler ve booksort.dll adlı tek bir derleme oluşturur.  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XslCompiledTransform>  
- [Nasıl yapılır: Derleme Kullanarak XSLT Dönüşümü Gerçekleştirme](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
