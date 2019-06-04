---
title: Sürüme Dayanıklı Serileştirme Teknolojisi Örneği
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: 6c30c39848be02785b6b808ecf4af711c0c9e95d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483000"
---
# <a name="version-tolerant-serialization-technology-sample"></a>Sürüme Dayanıklı Serileştirme Teknolojisi Örneği
[Örneği indirin](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 Bu örnek .NET seri hale getirme sürümü tolerans özelliklerini gösterir. Örnek farklı sürümleri kullanan uygulamalar oluşturur bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> hale getirmek ve veri serisini kaldırmak için. Farklı bir türe sürümleri varlığını rağmen uygulamalar sorunsuz iletişim. Daha fazla bilgi için [sürüme dayanıklı serileştirme](../../../docs/standard/serialization/version-tolerant-serialization.md).  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>Komut istemi kullanarak örneği oluşturmak için  
  
1. Bir komut istemi penceresi açın ve örnek için dile özgü alt (altında uygulama V1 veya V2 uygulama) birine gidin.  
  
2. Tür **msbuild.exe \<sunucu > application.sln** komut satırında (burada \<ver > v1 veya v2).  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak için  
  
1. Dosya Gezgini'ni açın ve örnek için dile özgü alt birine gidin.  
  
2. Önceki adımda seçtiğiniz dizininin V1 uygulama alt gidin.  
  
3. Visual Studio'da dosyayı açmak V1 Application.sln simgesini çift tıklatın.  
  
4. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
5. V2 uygulama alt dizinine gidin ve V2 uygulama oluşturmak için yukarıdaki iki adımı yineleyin.  
  
 Uygulamaları varsayılan \bin veya \bin\debug'dır dizinlerde kendi ilgili proje dizinlerin oluşturulur.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1. Komut İstemi penceresinde örnek uygulamalar yapılandırıldığında seçtiğiniz dile özgü alt dizinine gidin.  
  
2. Tür **runme.cmd** iki uygulamanın aynı anda çalıştırmak için komut satırına.  
  
 Alternatif olarak, sıralı olarak çalıştırın ve yeni yürütülebilir dosyaları içeren dizinler gidin.  
  
> [!NOTE]
>  Örnek konsol uygulamaları oluşturur. Başlatma ve bunları çıktılarını görüntülemek için komut istemi penceresinde Çalıştır gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.IO.FileStream>
