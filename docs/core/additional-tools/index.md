---
title: ".NET core ek araçlar"
description: "Destekleyen ve .NET çekirdek işlevselliğini genişleten ek araçlar genel bakış."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2018
ms.topic: article
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 21fcc1190ee4586a8d7eb6fb8d63a7c312e63825
ms.sourcegitcommit: c1904b0437605a90e5aa65b4abd7e048000e349d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2018
---
# <a name="net-core-additional-tools"></a>.NET core ek araçlar

Bu bölümde destekleyen ve ek olarak .NET çekirdek işlevselliğini genişleten Araçlar listesini derler [.NET Core komut satırı arabirimi (CLI)](..\tools\index.md) araçları.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[WCF Web hizmeti başvuru aracı](wcf-web-service-reference-guide.md)

WCF Web hizmeti başvuru içinde ilk kez yapılan bir Visual Studio bağlı hizmeti sağlayıcısıdır [Visual Studio 2017 sürüm 15,5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools). Bu araç, bir web hizmeti geçerli çözümdeki bir ağ konumu veya WSDL dosya meta verileri alır ve web erişmek için kullanabileceğiniz Windows Communication Foundation (WCF) istemci proxy kodu içeren bir .NET Core uyumlu kaynak dosyası oluşturur hizmet.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML Serileştirici Oluşturucusu](xml-serializer-generator.md)

Gibi [Xml seri hale getirici Oluşturucu (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) .NET Framework için [Microsoft.XmlSerializer.Generator NuGet paketi](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) .NET Core ve .NET standart kitaplıkları için çözümüdür. XML serileştirme bütünleştirilmiş serileştirmek veya seri durumundan kullanarak bu tür nesneler XML serileştirme başlangıç performansını artırmak için bir derlemede bulunan türleri için oluşturduğu <xref:System.Xml.Serialization.XmlSerializer>.