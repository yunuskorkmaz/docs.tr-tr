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

- The [Logman](/windows-server/administration/windows-commands/logman) and [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) command-line tools, which are included with the Windows operating system.

- The [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools in the [Windows Performance Toolkit](/windows-hardware/test/wpt/). For more information about Xperf, see the [Windows Performance blog](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/).

CLR olay bilgilerini yakalamak için, CLR sağlayıcısı bilgisayarınıza yüklenmelidir. To confirm that the provider is installed, type `logman query providers` at the command prompt. Sağlayıcı listesi görüntülenir. Bu liste, sağlayıcılar gibi CLR sağlayıcısı için bir girdi içermelidir.

```output
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil) command-line tool. Komut istemi penceresini yönetici olarak açın. Change the prompt directory to the .NET Framework 4 folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ). Bu klasör, CLE-ETW.man dosyasını içerir. Komut isteminde, CLR sağlayıcısını yüklemek için aşağıdaki komutu yazın:

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a>CLR ETW olaylarını yakalama

You can use the [Logman](/windows-server/administration/windows-commands/logman) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) command-line tools to capture ETW events, and the [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools to decode the trace events.

Bir kullanıcının, günlüğü etkinleştirmek için üç şeyi belirtmesi gerekir:

- İletişim kurmak için sağlayıcı.

- 64 bitlik bir sayı, bir anahtar kümesini temsil eder. Her anahtar, açılabilen sağlayıcının olaylar kümesini temsil eder. Sayı, açmak için birleştirilmiş bir anahtar sözcük kümesini temsil eder.

- Günlüğe kaydetmek için bir düzeyi (ayrıntılı) temsil eden bir küçük numara. Düzey 1, en az ayrıntılı ve düzey 5, en ayrıntılı düzeydir. Düzey 0, sağlayıcıya özgü olan anlamında bir varsayılandır.

### <a name="to-capture-clr-etw-events-using-logman"></a>Logman kullanarak CLR ETW olaylarını yakalamak için

1. Komut isteminde, şunları yazın:

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     burada:

    - The `-p` parameter identifies the provider GUID.

    - `0x1CCBD` specifies the categories of events that will be raised.

    - `0x5` sets the level of logging (in this case, verbose (5)).

    - The `-ets` parameter instructs Logman to send commands to event tracing sessions.

    - The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.

2. Olayları günlüğe kaydetmeyi durdurmak için şunu yazın:

     `logman stop clrevents -ets`

     Bu komut, clrevents.etl adlı bir ikili izleme dosyası oluşturur.

### <a name="to-capture-clr-etw-events-using-xperf"></a>Xperf kullanarak CLR ETW olaylarını yakalamak için

1. Komut isteminde, şunları yazın:

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).

2. İzlemeyi durdurmak için aşağıdakileri yazın:

     `Xperf -stop clr`

     Bu komut, clrevents.etl adlı bir izleme dosyası oluşturur.

## <a name="viewing-clr-etw-events"></a>CLR ETW olaylarını görüntüleme

CLR ETW olaylarını görüntülemek için aşağıda listelenen komutları kullanın. For a description of the events, see [CLR ETW Events](clr-etw-events.md).

### <a name="to-view-clr-etw-events-using-tracerpt"></a>Tracerpt kullanarak CLR ETW olaylarını görüntülemek için

- Komut isteminde, şunları yazın:

     `tracerpt clrevents.etl`

     Bu komut iki dosya oluşturur: dumpfile.xml ve summary.txt. Dumpfile.xml dosyası tüm olayları listeler ve summary.txt, olayların bir özetini sunar.

### <a name="to-view-clr-etw-events-using-xperf"></a>Xperf kullanarak CLR ETW olaylarını görüntülemek için

- Komut isteminde, şunları yazın:

     `xperf clrevents.etl`

     Bu komut Xperf ETL dosya görüntüleyicisini açar. In this viewer, the CLR events show up in the **Generic Events** view. To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a>.etl dosyasını, virgülle ayrılmış değerler dosyasına dönüştürmek için

- Komut isteminde, şunları yazın:

     `xperf -i clrevents.etl -f clrevents.csv`

     Bu komut, olayları görüntüleyebileceğiniz bir virgülle ayrılmış değer (CSV) dosyası olarak dökeceğiniz XPerf'e neden olur. Çünkü farklı olaylar farklı alanlara sahiptir, bu CSV dosyası veriden önce birden fazla üstbilgi satırını içerir. Her satırın ilk alanı, hangi üstbilginin geri kalan alanları belirlemek için kullanılması gerektiğini gösteren olay türüdür.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Performance Toolkit](/windows-hardware/test/wpt/)
- [Ortak Dil Çalışma Zamanı Modülünde ETW Olayları](etw-events-in-the-common-language-runtime.md)
