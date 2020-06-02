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
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a>XML Şema Tanımı Aracı ve XML Serileştirme

XML şema tanımı Aracı ([XSD. exe)](xml-schema-definition-tool-xsd-exe.md)), Windows &reg; yazılım geliştirme SETI 'nin (SDK) bir parçası olarak .NET Framework araçları ile birlikte yüklenir. Aracı, öncelikle iki amaçları için tasarlanmıştır:  
  
- Belirli bir XML şeması tanım dili (XSD) şemaya uygun C# veya Visual Basic sınıf dosyaları oluşturmak için. Aracı bağımsız değişken olarak bir XML Şeması alır ve bir dizi içeren bir dosya çıkarır, sahip serileştirilmiş olduğunda sınıflar <xref:System.Xml.Serialization.XmlSerializer>, şemaya uygun. Aracının belirli bir şemaya uygun sınıflar oluşturmak için nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: sınıf ve XML şeması belgeleri oluşturmak IÇIN XML şema tanımı aracını kullanma](xml-schema-def-tool-gen.md).  
  
- Bir XML Şeması belge .dll dosyası ya da .exe dosyası oluşturmak için. Oluşturduğunuz veya öznitelikleri ile değiştirilmiş bir dosya kümesinin şemasını görmek için, XML şemasını oluşturmak için, DLL veya EXE ' yi araca bağımsız değişken olarak geçirin. Aracının bir sınıf kümesinden bir XML Schema Document oluşturmak için nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: sınıf ve XML şeması belgeleri oluşturmak IÇIN XML şema tanımı aracını kullanma](xml-schema-def-tool-gen.md).  
  
Aracı kullanma hakkında daha fazla bilgi için bkz. [XML şema tanımı Aracı (xsd. exe)](xml-schema-definition-tool-xsd-exe.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataSet>
- [XML Serileştirmeye Giriş](introducing-xml-serialization.md)
- [XML şema tanımı Aracı (xsd. exe)](xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Nasıl yapılır: Nesne Serileştirme](how-to-serialize-an-object.md)
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](how-to-deserialize-an-object.md)
- [Nasıl yapılır: Sınıflar ve XML Şeması Belgeleri Oluşturmak için XML Şema Tanımı Aracını Kullanma](xml-schema-def-tool-gen.md)
- [XML şeması bağlama desteği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))
