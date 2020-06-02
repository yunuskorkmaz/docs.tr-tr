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
ms.openlocfilehash: c88770403d4c2abfb5ce99f44ea1bec1f8337545
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279782"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="1a4a4-103">XML Şema Tanımı Aracı ve XML Serileştirme</span><span class="sxs-lookup"><span data-stu-id="1a4a4-103">The XML Schema Definition Tool and XML Serialization</span></span>

<span data-ttu-id="1a4a4-104">XML şema tanımı Aracı ([XSD. exe)](xml-schema-definition-tool-xsd-exe.md)), Windows &reg; yazılım geliştirme SETI 'nin (SDK) bir parçası olarak .NET Framework araçları ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-104">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows&reg; Software Development Kit (SDK).</span></span> <span data-ttu-id="1a4a4-105">Aracı, öncelikle iki amaçları için tasarlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="1a4a4-105">The tool is designed primarily for two purposes:</span></span>  
  
- <span data-ttu-id="1a4a4-106">Belirli bir XML şeması tanım dili (XSD) şemaya uygun C# veya Visual Basic sınıf dosyaları oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-106">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="1a4a4-107">Aracı bağımsız değişken olarak bir XML Şeması alır ve bir dizi içeren bir dosya çıkarır, sahip serileştirilmiş olduğunda sınıflar <xref:System.Xml.Serialization.XmlSerializer>, şemaya uygun.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-107">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="1a4a4-108">Aracının belirli bir şemaya uygun sınıflar oluşturmak için nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: sınıf ve XML şeması belgeleri oluşturmak IÇIN XML şema tanımı aracını kullanma](xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="1a4a4-108">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](xml-schema-def-tool-gen.md).</span></span>  
  
- <span data-ttu-id="1a4a4-109">Bir XML Şeması belge .dll dosyası ya da .exe dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-109">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="1a4a4-110">Oluşturduğunuz veya öznitelikleri ile değiştirilmiş bir dosya kümesinin şemasını görmek için, XML şemasını oluşturmak için, DLL veya EXE ' yi araca bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-110">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="1a4a4-111">Aracının bir sınıf kümesinden bir XML Schema Document oluşturmak için nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: sınıf ve XML şeması belgeleri oluşturmak IÇIN XML şema tanımı aracını kullanma](xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="1a4a4-111">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](xml-schema-def-tool-gen.md).</span></span>  
  
<span data-ttu-id="1a4a4-112">Aracı kullanma hakkında daha fazla bilgi için bkz. [XML şema tanımı Aracı (xsd. exe)](xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1a4a4-112">For more information about using the tool, see [XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a4a4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-113">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="1a4a4-114">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="1a4a4-114">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="1a4a4-115">XML şema tanımı Aracı (xsd. exe)</span><span class="sxs-lookup"><span data-stu-id="1a4a4-115">XML Schema Definition Tool (Xsd.exe)</span></span>](xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="1a4a4-116">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="1a4a4-116">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="1a4a4-117">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="1a4a4-117">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
- [<span data-ttu-id="1a4a4-118">Nasıl yapılır: Sınıflar ve XML Şeması Belgeleri Oluşturmak için XML Şema Tanımı Aracını Kullanma</span><span class="sxs-lookup"><span data-stu-id="1a4a4-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](xml-schema-def-tool-gen.md)
- <span data-ttu-id="1a4a4-119">[XML şeması bağlama desteği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1a4a4-119">[XML Schema Binding Support](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span></span>
