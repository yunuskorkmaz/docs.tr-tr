---
title: SecAnnotate.exe (.NET Güvenlik Not Ekleyici Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f4712970b2d3ebecf12cbb7b8f9b7fcdb317986
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410357"
---
# <a name="secannotateexe-net-security-annotator-tool"></a>SecAnnotate.exe (.NET Güvenlik Not Ekleyici Aracı)
.NET güvenlik Not ekleyici Aracı (SecAnnotate.exe) tanımlayan bir komut satırı uygulamasıdır `SecurityCritical` ve `SecuritySafeCritical` bir veya daha fazla derlemeleri bölümlerini.  
  
 Visual Studio Uzantısı [güvenlik Not ekleyici](http://go.microsoft.com/fwlink/?LinkId=198007), SecAnnotate.exe için bir grafik kullanıcı arabirimi sağlar ve aracı Visual Studio'dan çalıştırmanıza olanak sağlar.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut isteminde, aşağıdakileri nerede *parametreleri* aşağıdaki bölümde açıklanan ve *derlemeleri* boşlukla ayrılmış bir veya daha fazla derleme adları oluşur:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
SecAnnotate.exe [parameters] [assemblies]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/a`<br /><br /> veya<br /><br /> `/showstatistics`|Analiz edilmekte olan derlemelerde saydamlık kullanımıyla ilgili istatistikleri gösterir.|  
|`/d:` *Dizin*<br /><br /> veya<br /><br /> `/referencedir:` *Dizin*|Ek açıklama sırasında bağımlı derlemelerin aranacağı bir dizin belirtir.|  
|`/i`<br /><br /> veya<br /><br /> `/includesignatures`|Ek açıklama raporu dosyasına genişletilmiş imza bilgileri ekler.|  
|`/n`<br /><br /> veya<br /><br /> `/nogac`|Genel derleme belleğinde başvurulan derlemelerin aranmasını bastırır.|  
|`/o:` *Output.XML*<br /><br /> veya<br /><br /> `/out:` *Output.XML*|Çıktı ek açıklama dosyasını belirtir.|  
|`/p:` *maxpasses*<br /><br /> veya<br /><br /> `/maximumpasses:` *maxpasses*|Yeni ek açıklamaların üretilmesini durdurmadan önce derlemelere yapılacak en fazla ek açıklama sayısını belirtir.|  
|`/q`<br /><br /> veya<br /><br /> `/quiet`|Açıklama ekleyicinin durum iletileri vermediği sessiz modu belirtir; yalnızca hata bilgilerini verir.|  
|`/r:` *Derleme*<br /><br /> veya<br /><br /> `/referenceassembly:` *Derleme*|Açıklama ekleme sırasında bağımlı derlemeleri çözerken, belirtilen derlemeyi ekler. Başvuru derlemelerine, başvuru yolunda bulunan derlemelere göre öncelik verilir.|  
|`/s:` *RuleName*<br /><br /> veya<br /><br /> `/suppressrule:` *RuleName*|Belirtilen saydamlık kuralını giriş derlemeleri üzerinde çalıştırmayı bastırır.|  
|`/t`<br /><br /> veya<br /><br /> `/forcetransparent`|Açıklama Ekleyici aracını, herhangi bir saydamlık ek açıklaması olmayan tüm derlemelere tümüyle saydamlarmış gibi davranmaya zorlar.|  
|`/t`:*derleme*<br /><br /> veya<br /><br /> `/forcetransparent`:*derleme*|Derleme düzeyindeki geçerli ek açıklamalarına bakılmaksızın, verilen derlemeyi saydam olmaya zorlar.|  
|||  
|`/v`<br /><br /> veya<br /><br /> `/verify`|Yalnızca bir derlemenin ek açıklamalarının doğru olduğunu doğrular; derleme doğrulamazsa, gerekli tüm ek açıklamaları bulmak için birden çok geçiş yapmayı denemez.|  
|`/x`<br /><br /> veya<br /><br /> `/verbose`|Ek açıklama eklerken ayrıntılı çıktı belirtir.|  
|`/y:` *Dizin*<br /><br /> veya<br /><br /> `/symbolpath:` *Dizin*|Açıklama ekleme sırasında simge dosyalarını ararken, belirtilen dizini ekler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Komut satırında belirtilen ve önüne bir at işareti (@) eklenen bir yanıt dosyasında parametreler ve derlemeler de sağlanabilir. Yanıt dosyasındaki her bir satır tek bir parametre veya derleme adı içermelidir.  
  
 Giriş .NET güvenlik Not ekleyici hakkında daha fazla bilgi için bkz: [kullanarak SecAnnotate saydamlık ihlalleri bilgisayarınızı derlemelerde çözümlemek için](http://go.microsoft.com/fwlink/?LinkId=187648) .NET güvenlik günlüğündeki.  
  
## <a name="examples"></a>Örnekler
