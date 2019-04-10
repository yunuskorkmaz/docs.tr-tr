---
title: .NET Framework Günlük Kaydını Denetleme
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16ed4d86d64a6d3c569c7fd7ab9e9e3a3943f078
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312104"
---
# <a name="controlling-net-framework-logging"></a>.NET Framework Günlük Kaydını Denetleme
Ortak dil çalışma zamanı (CLR) olaylarını izlemek için Windows olay izleme (ETW) kullanabilirsiniz. Aşağıdaki araçları kullanarak izlemeleri oluşturabilir ve görüntüleyebilirsiniz:  
  
-   [Logman](/windows-server/administration/windows-commands/logman) ve [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) komut satırı araçları, Windows işletim sistemiyle dahil edilir.  
  
-   [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) Araçları [Windows Performans Araç Seti](/windows-hardware/test/wpt/). Xperf hakkında daha fazla bilgi için bkz: [Windows Performans blogu](https://go.microsoft.com/fwlink/?LinkId=179509).  
  
 CLR olay bilgilerini yakalamak için, CLR sağlayıcısı bilgisayarınıza yüklenmelidir. Sağlayıcı'nın yüklü olduğunu doğrulamak için şunu yazın `logman query providers` komut isteminde. Sağlayıcı listesi görüntülenir. Bu liste, sağlayıcılar gibi CLR sağlayıcısı için bir girdi içermelidir.  
  
```  
Provider                                 GUID  
-------------------------------------------------------------------------------  
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.  
```  
  
 CLR sağlayıcı listede yoksa, Windows Vista ve sonraki işletim sistemlerinde Windows kullanarak yükleyebilirsiniz [Wevtutil](/windows-server/administration/windows-commands/wevtutil) komut satırı aracı. Komut istemi penceresini yönetici olarak açın. Komut istemi dizine geçin [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] klasörünü (% WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET sürüm>\ ). Bu klasör, CLE-ETW.man dosyasını içerir. Komut isteminde, CLR sağlayıcısını yüklemek için aşağıdaki komutu yazın:  
  
 `wevtutil im CLR-ETW.man`  
  
## <a name="capturing-clr-etw-events"></a>CLR ETW olaylarını yakalama  
 Kullanabileceğiniz [Logman](/windows-server/administration/windows-commands/logman) ve [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) ETW olaylarını yakalamak için komut satırı araçları ve [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) ve [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) kodunu çözmek için Araçlar izleme olayları.  
  
 Bir kullanıcının, günlüğü etkinleştirmek için üç şeyi belirtmesi gerekir:  
  
-   İletişim kurmak için sağlayıcı.  
  
-   64 bitlik bir sayı, bir anahtar kümesini temsil eder. Her anahtar, açılabilen sağlayıcının olaylar kümesini temsil eder. Sayı, açmak için birleştirilmiş bir anahtar sözcük kümesini temsil eder.  
  
-   Günlüğe kaydetmek için bir düzeyi (ayrıntılı) temsil eden bir küçük numara. Düzey 1, en az ayrıntılı ve düzey 5, en ayrıntılı düzeydir. Düzey 0, sağlayıcıya özgü olan anlamında bir varsayılandır.  
  
#### <a name="to-capture-clr-etw-events-using-logman"></a>Logman kullanarak CLR ETW olaylarını yakalamak için  
  
1. Komut isteminde, şunları yazın:  
  
     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`  
  
     burada:  
  
    -   `-p` Parametresi GUID sağlayıcısı tanımlar.  
  
    -   `0x1CCBD` Görüntülenecek olayların kategorilerini belirler.  
  
    -   `0x5` (Bu durumda, ayrıntılı (5)) günlüğe kaydetme düzeyini ayarlar.  
  
    -   `-ets` Parametresi, olay izleme oturumları için komutları göndermek için Logman'ı talimatı verir.  
  
    -   `-ct perf` Parametresi belirtir `QueryPerformanceCounter` işlevi, her olay için zaman damgasını oturum için kullanılacak.  
  
2. Olayları günlüğe kaydetmeyi durdurmak için şunu yazın:  
  
     `logman stop clrevents -ets`  
  
     Bu komut, clrevents.etl adlı bir ikili izleme dosyası oluşturur.  
  
#### <a name="to-capture-clr-etw-events-using-xperf"></a>Xperf kullanarak CLR ETW olaylarını yakalamak için  
  
1. Komut isteminde, şunları yazın:  
  
     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`  
  
     GUID, CLR ETW sağlayıcısı GUID olduğunda ve `0x1CCBD:5` adresindeki ve Düzey 5 (ayrıntılı) altındaki her şeyi izler.  
  
2. İzlemeyi durdurmak için aşağıdakileri yazın:  
  
     `Xperf -stop clr`  
  
     Bu komut, clrevents.etl adlı bir izleme dosyası oluşturur.  
  
## <a name="viewing-clr-etw-events"></a>CLR ETW olaylarını görüntüleme  
 CLR ETW olaylarını görüntülemek için aşağıda listelenen komutları kullanın. Olay açıklaması için bkz [CLR ETW olaylarını](../../../docs/framework/performance/clr-etw-events.md).  
  
#### <a name="to-view-clr-etw-events-using-tracerpt"></a>Tracerpt kullanarak CLR ETW olaylarını görüntülemek için  
  
-   Komut isteminde, şunları yazın:  
  
     `tracerpt clrevents.etl`  
  
     Bu komut iki dosya oluşturur: dumpfile.xml ve summary.txt. Dumpfile.xml dosyası tüm olayları listeler ve summary.txt, olayların bir özetini sunar.  
  
#### <a name="to-view-clr-etw-events-using-xperf"></a>Xperf kullanarak CLR ETW olaylarını görüntülemek için  
  
-   Komut isteminde, şunları yazın:  
  
     `xperf clrevents.etl`  
  
     Bu komut Xperf ETL dosya görüntüleyicisini açar. Bu görüntüleyicide, CLR olayları görünür **genel olaylar** görünümü. Türüne göre kategorilere ayrılmış olayların veri kılavuzunu görüntülemek için bu görünümde bir zaman bölgesi seçin ve ardından sağ tıklayıp **özeti**.  
  
#### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a>.etl dosyasını, virgülle ayrılmış değerler dosyasına dönüştürmek için  
  
-   Komut isteminde, şunları yazın:  
  
     `xperf -i clrevents.etl -f clrevents.csv`  
  
     Bu komut, olayları görüntüleyebileceğiniz bir virgülle ayrılmış değer (CSV) dosyası olarak dökeceğiniz XPerf'e neden olur. Çünkü farklı olaylar farklı alanlara sahiptir, bu CSV dosyası veriden önce birden fazla üstbilgi satırını içerir. Her satırın ilk alanı, hangi üstbilginin geri kalan alanları belirlemek için kullanılması gerektiğini gösteren olay türüdür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Performans Araç Seti](/windows-hardware/test/wpt/)
- [Ortak Dil Çalışma Zamanında ETW Olayları](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
