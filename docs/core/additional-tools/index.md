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
ms.openlocfilehash: eac67285500e62501f3bb552deaf5b07db609d4e
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2018
---
# <a name="net-core-additional-tools"></a><span data-ttu-id="fafc0-103">.NET core ek araçlar</span><span class="sxs-lookup"><span data-stu-id="fafc0-103">.NET Core additional tools</span></span>
<span data-ttu-id="fafc0-104">Bu bölümde destekleyen ve ek olarak .NET çekirdek işlevselliğini genişleten Araçlar listesini derler [.NET Core komut satırı arabirimi (CLI)](..\tools\index.md) araçları.</span><span class="sxs-lookup"><span data-stu-id="fafc0-104">This section compiles a list of tools that support and extend the .NET Core functionality, in addition to the [.NET Core command-line interface (CLI)](..\tools\index.md) tools.</span></span>

### <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[<span data-ttu-id="fafc0-105">WCF Web hizmeti başvuru aracı</span><span class="sxs-lookup"><span data-stu-id="fafc0-105">WCF Web Service Reference Tool</span></span>](wcf-web-service-reference-guide.md)
<span data-ttu-id="fafc0-106">WCF Web hizmeti başvuru içinde ilk kez yapılan bir Visual Studio bağlı hizmeti sağlayıcısıdır [Visual Studio 2017 sürüm 15,5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools).</span><span class="sxs-lookup"><span data-stu-id="fafc0-106">The WCF Web Service Reference is a Visual Studio connected service provider that made its debut in [Visual Studio 2017 version 15.5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools).</span></span> <span data-ttu-id="fafc0-107">Bu araç, bir web hizmeti geçerli çözümdeki bir ağ konumu veya WSDL dosya meta verileri alır ve web erişmek için kullanabileceğiniz Windows Communication Foundation (WCF) istemci proxy kodu içeren bir .NET Core uyumlu kaynak dosyası oluşturur hizmet.</span><span class="sxs-lookup"><span data-stu-id="fafc0-107">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

### <a name="xml-serializer-generatorxmlserializergenerator-instructionsmd"></a>[<span data-ttu-id="fafc0-108">XML seri hale getirici Oluşturucusu</span><span class="sxs-lookup"><span data-stu-id="fafc0-108">XML Serializer Generator</span></span>](xmlserializergenerator-instructions.md)
<span data-ttu-id="fafc0-109">Gibi [Xml seri hale getirici Oluşturucu (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) .NET Framework için [Microsoft.XmlSerializer.Generator NuGet paketi](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) .NET Core ve .NET standart kitaplıkları için çözümüdür.</span><span class="sxs-lookup"><span data-stu-id="fafc0-109">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the solution for .NET Core and .NET Standard libraries.</span></span> <span data-ttu-id="fafc0-110">XML serileştirme bütünleştirilmiş serileştirmek veya seri durumundan kullanarak bu tür nesneler XML serileştirme başlangıç performansını artırmak için bir derlemede bulunan türleri için oluşturduğu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fafc0-110">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>
