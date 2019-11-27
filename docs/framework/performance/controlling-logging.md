---
title: .NET Framework Günlük Kaydını Denetleme
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 924d209cd1177ffc1702ebe958c58bfc29c22c38
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447682"
---
# <a name="controlling-net-framework-logging"></a>.NET Framework Günlük Kaydını Denetleme

Ortak dil çalışma zamanı (CLR) olaylarını izlemek için Windows olay izleme (ETW) kullanabilirsiniz. Aşağıdaki araçları kullanarak izlemeleri oluşturabilir ve görüntüleyebilirsiniz:

- Windows işletim sistemine dahil olan [Logman](/windows-server/administration/windows-commands/logman) ve [tracerpt](/windows-server/administration/windows-commands/tracerpt_1) komut satırı araçları.

- [Windows performans araç seti](/windows-hardware/test/wpt/)'Nde [XPerf](/windows-hardware/test/wpt/xperf-command-line-reference) araçları. XPerf hakkında daha fazla bilgi için [Windows performans blogu](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/)' na bakın.

CLR olay bilgilerini yakalamak için, CLR sağlayıcısı bilgisayarınıza yüklenmelidir. Sağlayıcının yüklendiğini doğrulamak için komut istemine `logman query providers` yazın. Sağlayıcı listesi görüntülenir. Bu liste, sağlayıcılar gibi CLR sağlayıcısı için bir girdi içermelidir.

```output
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

CLR sağlayıcısı listede yoksa, Windows [wevtutil](/windows-server/administration/windows-commands/wevtutil) komut satırı aracını kullanarak Windows Vista ve sonraki işletim sistemlerine yükleyebilirsiniz. Komut istemi penceresini yönetici olarak açın. İstem dizinini .NET Framework 4 klasörü olarak değiştirin (%WINDIR%\Microsoft.NET\Framework [64] \v4.\<.NET sürümü > \). Bu klasör, CLE-ETW.man dosyasını içerir. Komut isteminde, CLR sağlayıcısını yüklemek için aşağıdaki komutu yazın:

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a>CLR ETW olaylarını yakalama

ETW olaylarını yakalamak için [Logman](/windows-server/administration/windows-commands/logman) ve [XPerf](/windows-hardware/test/wpt/xperf-command-line-reference) komut satırı araçlarını ve izleme olaylarının kodunu çözmek Için [tracerpt](/windows-server/administration/windows-commands/tracerpt_1) ve [XPerf](/windows-hardware/test/wpt/xperf-command-line-reference) araçlarını kullanabilirsiniz.

Bir kullanıcının, günlüğü etkinleştirmek için üç şeyi belirtmesi gerekir:

- İletişim kurmak için sağlayıcı.

- 64 bitlik bir sayı, bir anahtar kümesini temsil eder. Her anahtar, açılabilen sağlayıcının olaylar kümesini temsil eder. Sayı, açmak için birleştirilmiş bir anahtar sözcük kümesini temsil eder.

- Günlüğe kaydetmek için bir düzeyi (ayrıntılı) temsil eden bir küçük numara. Düzey 1, en az ayrıntılı ve düzey 5, en ayrıntılı düzeydir. Düzey 0, sağlayıcıya özgü olan anlamında bir varsayılandır.

### <a name="to-capture-clr-etw-events-using-logman"></a>Logman kullanarak CLR ETW olaylarını yakalamak için

1. Komut isteminde, şunları yazın:

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     burada:

    - `-p` parametresi, sağlayıcı GUID 'INI tanımlar.

    - `0x1CCBD`, oluşturulacak olayların kategorilerini belirtir.

    - `0x5` günlük düzeyini (Bu durumda verbose (5)) ayarlar.

    - `-ets` parametresi, Logman 'yi olay izleme oturumlarına komut gönderecek şekilde yönlendirir.

    - `-ct perf` parametresi, `QueryPerformanceCounter` işlevinin her olay için zaman damgasını günlüğe kaydetmek için kullanılacağını belirtir.

2. Olayları günlüğe kaydetmeyi durdurmak için şunu yazın:

     `logman stop clrevents -ets`

     Bu komut, clrevents.etl adlı bir ikili izleme dosyası oluşturur.

### <a name="to-capture-clr-etw-events-using-xperf"></a>Xperf kullanarak CLR ETW olaylarını yakalamak için

1. Komut isteminde, şunları yazın:

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     burada GUID, CLR ETW sağlayıcısı GUID 'sidir ve `0x1CCBD:5` her şeyi 5. düzey (verbose) ' de izler.

2. İzlemeyi durdurmak için aşağıdakileri yazın:

     `Xperf -stop clr`

     Bu komut, clrevents.etl adlı bir izleme dosyası oluşturur.

## <a name="viewing-clr-etw-events"></a>CLR ETW olaylarını görüntüleme

CLR ETW olaylarını görüntülemek için aşağıda listelenen komutları kullanın. Olayların açıklaması için bkz. [CLR ETW olayları](clr-etw-events.md).

### <a name="to-view-clr-etw-events-using-tracerpt"></a>Tracerpt kullanarak CLR ETW olaylarını görüntülemek için

- Komut isteminde, şunları yazın:

     `tracerpt clrevents.etl`

     Bu komut iki dosya oluşturur: dumpfile.xml ve summary.txt. Dumpfile.xml dosyası tüm olayları listeler ve summary.txt, olayların bir özetini sunar.

### <a name="to-view-clr-etw-events-using-xperf"></a>Xperf kullanarak CLR ETW olaylarını görüntülemek için

- Komut isteminde, şunları yazın:

     `xperf clrevents.etl`

     Bu komut Xperf ETL dosya görüntüleyicisini açar. Bu görüntüleyicide, CLR olayları **Genel olaylar** görünümünde görünür. Türe göre kategorize edilmiş olayların veri kılavuzunu görüntülemek için, bu görünümdeki bir zaman bölgesi seçin ve ardından sağ tıklayıp **Özet**' i seçin.

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a>.etl dosyasını, virgülle ayrılmış değerler dosyasına dönüştürmek için

- Komut isteminde, şunları yazın:

     `xperf -i clrevents.etl -f clrevents.csv`

     Bu komut, olayları görüntüleyebileceğiniz bir virgülle ayrılmış değer (CSV) dosyası olarak dökeceğiniz XPerf'e neden olur. Çünkü farklı olaylar farklı alanlara sahiptir, bu CSV dosyası veriden önce birden fazla üstbilgi satırını içerir. Her satırın ilk alanı, hangi üstbilginin geri kalan alanları belirlemek için kullanılması gerektiğini gösteren olay türüdür.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows performans araç seti](/windows-hardware/test/wpt/)
- [Ortak Dil Çalışma Zamanı Modülünde ETW Olayları](etw-events-in-the-common-language-runtime.md)
