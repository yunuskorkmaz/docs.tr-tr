---
title: XML Şema Tanımı Aracı ve XML Serileştirme
description: XML şema tanımı aracı bir XSD şeması için C# veya Visual Basic sınıf dosyaları oluşturur ve bir kitaplıktan veya yürütülebilir dosyadan bir XML şeması oluşturur.
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: 258e66643dae64aec7280419911f5ac9193a2ada
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380108"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="1f8be-103">XML Şema Tanımı Aracı ve XML Serileştirme</span><span class="sxs-lookup"><span data-stu-id="1f8be-103">The XML Schema Definition Tool and XML Serialization</span></span>

<span data-ttu-id="1f8be-104">XML şema tanımı Aracı ([XSD. exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)), Windows &reg; yazılım geliştirme SETI 'nin (SDK) bir parçası olarak .NET Framework araçları ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1f8be-104">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows&reg; Software Development Kit (SDK).</span></span> <span data-ttu-id="1f8be-105">Aracı, öncelikle iki amaçları için tasarlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="1f8be-105">The tool is designed primarily for two purposes:</span></span>  
  
- <span data-ttu-id="1f8be-106">Belirli bir XML şeması tanım dili (XSD) şemaya uygun C# veya Visual Basic sınıf dosyaları oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="1f8be-106">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="1f8be-107">Aracı bağımsız değişken olarak bir XML Şeması alır ve bir dizi içeren bir dosya çıkarır, sahip serileştirilmiş olduğunda sınıflar <xref:System.Xml.Serialization.XmlSerializer>, şemaya uygun.</span><span class="sxs-lookup"><span data-stu-id="1f8be-107">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="1f8be-108">Aracının belirli bir şemaya uygun sınıflar oluşturmak için nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: sınıf ve XML şeması belgeleri oluşturmak IÇIN XML şema tanımı aracını kullanma](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="1f8be-108">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
- <span data-ttu-id="1f8be-109">Bir XML Şeması belge .dll dosyası ya da .exe dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="1f8be-109">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="1f8be-110">Oluşturduğunuz veya öznitelikleri ile değiştirilmiş bir dosya kümesinin şemasını görmek için, XML şemasını oluşturmak için, DLL veya EXE ' yi araca bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="1f8be-110">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="1f8be-111">Aracının bir sınıf kümesinden bir XML Schema Document oluşturmak için nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: sınıf ve XML şeması belgeleri oluşturmak IÇIN XML şema tanımı aracını kullanma](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="1f8be-111">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
<span data-ttu-id="1f8be-112">Aracı kullanma hakkında daha fazla bilgi için bkz. [XML şema tanımı Aracı (xsd. exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1f8be-112">For more information about using the tool, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f8be-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f8be-113">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="1f8be-114">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="1f8be-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="1f8be-115">XML şema tanımı Aracı (xsd. exe)</span><span class="sxs-lookup"><span data-stu-id="1f8be-115">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="1f8be-116">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="1f8be-116">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="1f8be-117">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="1f8be-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="1f8be-118">Nasıl yapılır: Sınıflar ve XML Şeması Belgeleri Oluşturmak için XML Şema Tanımı Aracını Kullanma</span><span class="sxs-lookup"><span data-stu-id="1f8be-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)
- <span data-ttu-id="1f8be-119">[XML şeması bağlama desteği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1f8be-119">[XML Schema Binding Support](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span></span>
