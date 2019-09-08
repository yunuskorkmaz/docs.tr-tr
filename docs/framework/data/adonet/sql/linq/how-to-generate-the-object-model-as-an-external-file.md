---
title: 'Nasıl yapılır: Nesne Modelini Dış Dosya Olarak Oluşturma'
ms.date: 03/30/2017
ms.assetid: 2496fa06-3df4-4ecb-86c4-70a49ea08565
ms.openlocfilehash: 3fd84d878ab07411bba41a13ff3eef91b2425e8a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793590"
---
# <a name="how-to-generate-the-object-model-as-an-external-file"></a>Nasıl yapılır: Nesne Modelini Dış Dosya Olarak Oluşturma
Öznitelik tabanlı eşlemeye alternatif olarak, SQLMetal komut satırı aracını kullanarak nesne modelinizi harici bir XML dosyası olarak oluşturabilirsiniz. Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md). Harici bir XML eşleme dosyası kullanarak kodunuzda dağınıklığı azaltabilirsiniz. Ayrıca, uygulamanızın ikili dosyalarını yeniden derlemeden dış dosyayı değiştirerek davranışı değiştirebilirsiniz. Daha fazla bilgi için bkz. [dış eşleme](external-mapping.md).  
  
> [!NOTE]
> Nesne İlişkisel Tasarımcısı bir dış eşleme dosyası oluşturmayı desteklemez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, Northwind örnek veritabanından bir dış eşleme dosyası oluşturur.  
  
```  
sqlmetal /server:myserver /database:northwind /map:externalfile.xml  
```  
  
## <a name="example"></a>Örnek  
 Bir dış eşleme dosyasından aşağıdaki alıntı, Northwind örnek veritabanındaki Customers tablosunun eşlemesini gösterir. Bu alıntı, **/Map** seçeneği Ile SqlMetal yürütülerek oluşturulmuştur.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Database xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" Name="northwnd">  
  <Table Name="Customers">  
    <Type Name=".Customer">  
      <Column Name="CustomerID" Member="CustomerID" Storage="_CustomerID" DbType="NChar(5) NOT NULL" CanBeNull="False" IsPrimaryKey="True" />  
      <Column Name="CompanyName" Member="CompanyName" Storage="_CompanyName" DbType="NVarChar(40) NOT NULL" CanBeNull="False" />  
      <Column Name="ContactName" Member="ContactName" Storage="_ContactName" DbType="NVarChar(30)" />  
      <Column Name="ContactTitle" Member="ContactTitle" Storage="_ContactTitle" DbType="NVarChar(30)" />  
      <Column Name="Address" Member="Address" Storage="_Address" DbType="NVarChar(60)" />  
      <Column Name="City" Member="City" Storage="_City" DbType="NVarChar(15)" />  
      <Column Name="Region" Member="Region" Storage="_Region" DbType="NVarChar(15)" />  
      <Column Name="PostalCode" Member="PostalCode" Storage="_PostalCode" DbType="NVarChar(10)" />  
      <Column Name="Country" Member="Country" Storage="_Country" DbType="NVarChar(15)" />  
      <Column Name="Phone" Member="Phone" Storage="_Phone" DbType="NVarChar(24)" />  
      <Column Name="Fax" Member="Fax" Storage="_Fax" DbType="NVarChar(24)" />  
      <Association Name="FK_CustomerCustomerDemo_Customers" Member="CustomerCustomerDemos" Storage="_CustomerCustomerDemos" ThisKey="CustomerID" OtherTable="CustomerCustomerDemo" OtherKey="CustomerID" DeleteRule="NO ACTION" />  
      <Association Name="FK_Orders_Customers" Member="Orders" Storage="_Orders" ThisKey="CustomerID" OtherTable="Orders" OtherKey="CustomerID" DeleteRule="NO ACTION" />  
    </Type>  
  </Table>  
</Database>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Modeli Oluşturma](creating-the-object-model.md)
- [Dış Eşleme](external-mapping.md)
- [Nasıl yapılır: Visual Basic veya içinde nesne modeli oluşturmaC#](how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
