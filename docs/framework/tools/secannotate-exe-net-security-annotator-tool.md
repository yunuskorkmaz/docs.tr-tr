---
title: SecAnnotate.exe (.NET Güvenlik Not Ekleyici Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
ms.openlocfilehash: ffc275c588775fb79da276be904ada90a5a31bad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937921"
---
# <a name="secannotateexe-net-security-annotator-tool"></a>SecAnnotate.exe (.NET Güvenlik Not Ekleyici Aracı)
.NET Security Ek Açıklama aracı (SecAnnotate.exe), bir veya daha `SecurityCritical` fazla `SecuritySafeCritical` derlemenin bölümlerini ve bölümlerini tanımlayan bir komut satırı uygulamasıdır.  
  
 Bir Visual Studio uzantısı, [Güvenlik Açıklama ,](https://marketplace.visualstudio.com/items?itemName=sheldonb.SecurityAnnotator)SecAnnotate.exe bir grafik kullanıcı arayüzü sağlar ve Visual Studio aracı çalıştırmak için sağlar.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
 Komut isteminde, *parametrelerin* aşağıdaki bölümde açıklandığı ve *derlemelerin* boşluklarla ayrılmış bir veya daha fazla derleme adı olduğu aşağıdakileri yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
SecAnnotate.exe [parameters] [assemblies]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/a`<br /><br /> or<br /><br /> `/showstatistics`|Analiz edilmekte olan derlemelerde saydamlık kullanımıyla ilgili istatistikleri gösterir.|  
|`/d:`*dizin*<br /><br /> or<br /><br /> `/referencedir:`*dizin*|Ek açıklama sırasında bağımlı derlemelerin aranacağı bir dizin belirtir.|  
|`/i`<br /><br /> or<br /><br /> `/includesignatures`|Ek açıklama raporu dosyasına genişletilmiş imza bilgileri ekler.|  
|`/n`<br /><br /> or<br /><br /> `/nogac`|Genel derleme belleğinde başvurulan derlemelerin aranmasını bastırır.|  
|`/o:`*output.xml*<br /><br /> or<br /><br /> `/out:`*output.xml*|Çıktı ek açıklama dosyasını belirtir.|  
|`/p:`*maxpasses*<br /><br /> or<br /><br /> `/maximumpasses:`*maxpasses*|Yeni ek açıklamaların üretilmesini durdurmadan önce derlemelere yapılacak en fazla ek açıklama sayısını belirtir.|  
|`/q`<br /><br /> or<br /><br /> `/quiet`|Açıklama ekleyicinin durum iletileri vermediği sessiz modu belirtir; yalnızca hata bilgilerini verir.|  
|`/r:`*montaj*<br /><br /> or<br /><br /> `/referenceassembly:`*montaj*|Açıklama ekleme sırasında bağımlı derlemeleri çözerken, belirtilen derlemeyi ekler. Başvuru derlemelerine, başvuru yolunda bulunan derlemelere göre öncelik verilir.|  
|`/s:`*kural adı*<br /><br /> or<br /><br /> `/suppressrule:`*kural adı*|Belirtilen saydamlık kuralını giriş derlemeleri üzerinde çalıştırmayı bastırır.|  
|`/t`<br /><br /> or<br /><br /> `/forcetransparent`|Açıklama Ekleyici aracını, herhangi bir saydamlık ek açıklaması olmayan tüm derlemelere tümüyle saydamlarmış gibi davranmaya zorlar.|  
|`/t`:*montaj*<br /><br /> or<br /><br /> `/forcetransparent`:*montaj*|Derleme düzeyindeki geçerli ek açıklamalarına bakılmaksızın, verilen derlemeyi saydam olmaya zorlar.|  
|||  
|`/v`<br /><br /> or<br /><br /> `/verify`|Yalnızca bir derlemenin ek açıklamalarının doğru olduğunu doğrular; derleme doğrulamazsa, gerekli tüm ek açıklamaları bulmak için birden çok geçiş yapmayı denemez.|  
|`/x`<br /><br /> or<br /><br /> `/verbose`|Ek açıklama eklerken ayrıntılı çıktı belirtir.|  
|`/y:`*dizin*<br /><br /> or<br /><br /> `/symbolpath:`*dizin*|Açıklama ekleme sırasında simge dosyalarını ararken, belirtilen dizini ekler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Komut satırında belirtilen ve önüne bir at işareti (@) eklenen bir yanıt dosyasında parametreler ve derlemeler de sağlanabilir. Yanıt dosyasındaki her bir satır tek bir parametre veya derleme adı içermelidir.  
  
 .NET Security Ek Açıklama hakkında daha fazla bilgi için, .NET Security blogunda .NET Security blogunda,.NET Güvenlik blogunda [Derlemelerinizi Analiz Etmek için SecAnnotate'yi kullanarak](https://docs.microsoft.com/archive/blogs/shawnfa/using-secannotate-to-analyze-your-assemblies-for-transparency-violations-an-example) girişe bakın.  
  
## <a name="examples"></a>Örnekler
