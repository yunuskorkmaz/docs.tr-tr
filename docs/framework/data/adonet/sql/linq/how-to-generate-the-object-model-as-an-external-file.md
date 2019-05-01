---
title: 'Nasıl yapılır: Nesne Modelini Dış Dosya Olarak Oluşturma'
ms.date: 03/30/2017
ms.assetid: 2496fa06-3df4-4ecb-86c4-70a49ea08565
ms.openlocfilehash: 2e439cd6628daa5b574be2049393dc2964896679
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033754"
---
# <a name="how-to-generate-the-object-model-as-an-external-file"></a>Nasıl yapılır: Nesne Modelini Dış Dosya Olarak Oluşturma
Öznitelik tabanlı eşleme için alternatif olarak, nesne modeli, dış bir XML dosyası olarak SQLMetal komut satırı aracını kullanarak oluşturabilirsiniz. Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). Dış XML eşleme dosyası kullanarak kodunuzda dağınıklığını azaltın. Ayrıca, uygulamanızın ikili dosyaları yeniden derlemeye gerek kalmadan dış dosyasını değiştirerek davranışını değiştirebilirsiniz. Daha fazla bilgi için [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
> [!NOTE]
>  [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Dış eşleme dosyasının oluşturulmasını desteklemiyor.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, Northwind örnek veritabanındaki bir dış eşleme dosyası oluşturur.  
  
```  
sqlmetal /server:myserver /database:northwind /map:externalfile.xml  
```  
  
## <a name="example"></a>Örnek  
 Bir dış eşleme dosyası alınan aşağıdaki alıntıda Northwind örnek veritabanındaki Müşteriler tablosu için eşlemeyi gösterir. SQLMetal ile çalıştırarak bu alıntı oluşturulan **/map** seçeneği.  
  
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

- [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Dış Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [Nasıl yapılır: Visual Basic'de nesne modeli oluşturmak veyaC#](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
