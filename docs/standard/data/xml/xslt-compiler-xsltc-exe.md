---
title: XSLT derleyici (xsltc.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2b4ede7bdb8dad65e9cd959dfaa2f8956a877762
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xslt-compiler-xsltcexe"></a>XSLT derleyici (xsltc.exe)
XSLT derleyici (xsltc.exe) XSLT stil sayfaları derler ve bir derleme oluşturur. Derlenmiş stil sayfası ardından doğrudan geçirilebilir <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemi. İmzalı derlemeler xsltc.exe ile oluşturulamıyor.  
  
 Visual Studio 2008'de bulunan xsltc.exe aracıdır. Daha fazla bilgi için bkz: [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=89463).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a>Bağımsız Değişken  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`sourceFile`|Stil sayfasının adı belirtir. Stil sayfası veya intranette bulunan bir yerel dosya olmalıdır.|  
  
## <a name="options"></a>Seçenekler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/c[lass]:``name`|Aşağıdaki stil sayfası sınıfın adını belirtir. Sınıf adı tam olabilir.<br /><br /> Sınıf adı varsayılan olarak stil sayfasının adı. Örneğin, stil sayfası customers.xsl derlenmiş ise varsayılan sınıf adını müşterileri içindir.|  
|`/debug[`+&#124;-`]`|Hata ayıklama bilgilerini oluşturulup oluşturulmayacağını belirtir.<br /><br /> Belirtme `+` veya `/debug`, hata ayıklama bilgileri oluşturmak ve bir program veritabanı (PDB) dosyasında yerleştirin derleyicinin neden olur. Oluşturulan PDB dosyası adı `assemblyName`.pdb.<br /><br /> Belirtme `-`, hangi değil belirtirseniz yürürlükte olan `/debug`, hiçbir hata ayıklama bilgisi oluşturulmasına neden olur. Bir perakende derleme oluşturulur. **Not:** hata ayıklama modunda derleme etkileyebilecek XSLT performansı önemli ölçüde.|  
|`/help`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`/nologo`|Görüntülenmesini Derleyici telif hakkı iletisi gizler.|  
|`/platform:``string`|Derleme çalıştırılabilir platformları belirtir. Geçerli platform değerleri açıklanmaktadır:<br /><br /> `x86`32-bit, x86 uyumlu ortak dil çalışma zamanı tarafından çalıştırılacak derlemenizi<br /><br /> `x64`AMD64 veya EM64T yönerge kümesi destekleyen bir bilgisayarda 64-bit ortak dil çalışma zamanı tarafından çalıştırılacak derlemenizi birleştirir.<br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)]derlemenizi olan bir bilgisayarda 64-bit ortak dil çalışma zamanı tarafından çalıştırılacak bir [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] işlemci.<br /><br /> `anycpu`herhangi bir platformda çalıştırılacak derlemenizi birleştirir. Bu varsayılandır.|  
|`/out:``assemblyName`|Çıkış bütünleştirilmiş kodun adını belirtir. Birden çok stil sayfaları varsa ana stil sayfası veya ilk stil sayfası adını derleme adı varsayılan olarak ayarlanır.<br /><br /> Stil sayfası komut dosyaları içeriyorsa, komut dosyaları için ayrı bir derleme kaydedilir. Komut dosyası derleme adları ana derleme adından üretilir. Örneğin, CustOrders.dll için derleme adınızı belirttiyseniz, ilk komut dosyası derleme CustOrders_Script1.dll olarak adlandırılır.|  
|`/settings:``document+-, script+-, DTD+-,`|İzin verilip verilmeyeceğini belirtir `document()` İşlevler, XSLT komut dosyası veya belge stil sayfanızda tanımı (DTD) yazın.<br /><br /> DTD desteği varsayılan davranışı devre dışı bırakır `document()` işlevi ve komut dosyası.|  
|`@``file`|Derleyici seçenekleri içeren bir dosyayı belirtmenize olanak sağlar.|  
|`?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 XSLT çözümleri birden çok stil sayfası modüllerini oluşabilir. Xsltc.exe aracı derlemeleri stil sayfalarını oluşturur. Derlemeleri sonra içine aktarılabilecek <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemi. Bu, bazı XSLT dağıtım senaryolarında performans maliyetleri azaltmak yardımcı olabilir.  
  
> [!NOTE]
>  Uygulamanızda bir başvuru olarak derlenmiş derleme de dahil etmelisiniz.  
  
 Xsltc.exe araç sınıfı doğrulamaz (`/class:``name`) veya derleme (`/out:``assemblyName`) adları. Adları geçerli değilse, hatalar ortak dil çalışma zamanı tarafından atılır.  
  
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
  
 Aşağıdaki komut DTD işleme ve komut dosyası desteğini etkinleştirir ve myTest.dll ve myTest_Script1.dll adlı iki derlemeler oluşturur.  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 Aşağıdaki komut iki stil sayfası modülleri derler ve booksort.dll adlı tek bir bütünleştirilmiş kod oluşturur.  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [Nasıl yapılır: bir derlemeyi kullanarak XSLT dönüşümü gerçekleştirin](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
 [XSLT dönüştürmeleri](../../../../docs/standard/data/xml/xslt-transformations.md)
