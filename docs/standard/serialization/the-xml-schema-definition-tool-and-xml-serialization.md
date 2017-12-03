---
title: "XML şema tanımı aracı ve XML serileştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6bd462714ada242062c9e2e23f924868f5870ef8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="e5fae-102">XML şema tanımı aracı ve XML serileştirme</span><span class="sxs-lookup"><span data-stu-id="e5fae-102">The XML Schema Definition Tool and XML Serialization</span></span>
<span data-ttu-id="e5fae-103">XML şema tanımı Aracı'nı ([XML şema tanımı aracını (XSD.exe'nin)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) yanı sıra .NET Framework Araçları Windows® Yazılım Geliştirme Seti (SDK), bir parçası olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e5fae-103">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows® Software Development Kit (SDK).</span></span> <span data-ttu-id="e5fae-104">Aracı, öncelikle iki amaçları için tasarlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="e5fae-104">The tool is designed primarily for two purposes:</span></span>  
  
-   <span data-ttu-id="e5fae-105">Belirli bir XML şeması tanım dili (XSD) şemaya uygun C# veya Visual Basic sınıf dosyaları oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e5fae-105">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="e5fae-106">Aracı bağımsız değişken olarak bir XML Şeması alır ve bir dizi içeren bir dosya çıkarır, sahip serileştirilmiş olduğunda sınıflar <xref:System.Xml.Serialization.XmlSerializer>, şemaya uygun.</span><span class="sxs-lookup"><span data-stu-id="e5fae-106">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="e5fae-107">Aracının belirli bir şemaya uygun sınıfları oluşturmak için nasıl kullanılacağı hakkında daha fazla bilgi için bkz [nasıl yapılır: XML şema tanımı sınıfları oluşturmak ve XML Şeması belgelere aracını](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="e5fae-107">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
-   <span data-ttu-id="e5fae-108">Bir XML Şeması belge .dll dosyası ya da .exe dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e5fae-108">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="e5fae-109">Oluşturulan ya da sahip dosyalar ya da özniteliklerle değiştiren bir şema görmek için XML şeması oluşturmak için aracı bağımsız değişken olarak DLL veya EXE geçirin.</span><span class="sxs-lookup"><span data-stu-id="e5fae-109">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="e5fae-110">Aracının sınıfları kümesinden bir XML Şeması belgesi oluşturmak için nasıl kullanılacağı hakkında daha fazla bilgi için bkz [nasıl yapılır: XML şema tanımı sınıfları oluşturmak ve XML Şeması belgelere aracını](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="e5fae-110">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
 <span data-ttu-id="e5fae-111">Bu araç ve diğerleri hakkında daha fazla bilgi için bkz: [Araçları](../../../docs/framework/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="e5fae-111">For more information about this tool and others, see [Tools](../../../docs/framework/tools/index.md).</span></span> <span data-ttu-id="e5fae-112">Aracın seçenekleri hakkında daha fazla bilgi için bkz: [XML şema tanımı aracını (XSD.exe'nin)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e5fae-112">For information about the tool's options, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5fae-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5fae-113">See Also</span></span>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="e5fae-114">Giriş XML serileştirme</span><span class="sxs-lookup"><span data-stu-id="e5fae-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="e5fae-115">XML şema tanımı aracını (XSD.exe'nin)</span><span class="sxs-lookup"><span data-stu-id="e5fae-115">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="e5fae-116">Nasıl yapılır: bir nesneyi serileştirme</span><span class="sxs-lookup"><span data-stu-id="e5fae-116">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="e5fae-117">Nasıl yapılır: bir nesne seri durumdan</span><span class="sxs-lookup"><span data-stu-id="e5fae-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [<span data-ttu-id="e5fae-118">Nasıl yapılır: sınıfları ve XML Şeması belgeleri oluşturmak üzere XML şema tanımı aracını kullanın</span><span class="sxs-lookup"><span data-stu-id="e5fae-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)  
 [<span data-ttu-id="e5fae-119">.NET Framework Destek bağlama XML Şeması</span><span class="sxs-lookup"><span data-stu-id="e5fae-119">XML Schema Binding Support in the .NET Framework</span></span>](http://msdn.microsoft.com/en-us/8f0619dd-f1fc-4895-ae21-6d45d0382cc1)
