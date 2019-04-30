---
title: 'Nasıl yapılır: Yeni bir tür (LINQ to XML) proje (C#)'
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: eefe645f376f8f52a94b94cdd49640e165a69aae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667866"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Nasıl yapılır: Yeni bir tür (LINQ to XML) proje (C#)
Bu bölümdeki diğer örnekler, sonuç olarak döndüren sorgular gösterilmesini <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> , `string`, ve <xref:System.Collections.Generic.IEnumerable%601> , `int`. Bunlar ortak sonuç türleri, ancak her senaryo için uygun değildir. Çoğu durumda sorgularınızın döndürülecek isteyeceksiniz bir <xref:System.Collections.Generic.IEnumerable%601> başka bir tür.  
  
## <a name="example"></a>Örnek  
 Bu örnek nesneleri oluşturmak nasıl gösterir `select` yan tümcesi. Kod öncelikle bir oluşturucuya sahip yeni bir sınıf tanımlar ve sonra değiştirir `select` deyimi deyim yeni sınıfının yeni bir örneğini olmasını sağlayın.  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
class NameQty {  
    public string name;  
    public int qty;  
    public NameQty(string n, int q)  
    {  
        name = n;  
        qty = q;  
    }  
};  
  
class Program {  
    public static void Main() {  
        XElement po = XElement.Load("PurchaseOrder.xml");  
  
        IEnumerable<NameQty> nqList =  
            from n in po.Descendants("Item")  
            select new NameQty(  
                    (string)n.Element("ProductName"),  
                    (int)n.Element("Quantity")  
                );  
  
        foreach (NameQty n in nqList)  
            Console.WriteLine(n.name + ":" + n.qty);  
    }  
}  
```  
  
 Bu örnekte `M:System.Xml.Linq.XElement.Element` konu başlığı altında tanıtılan yöntemi [nasıl yapılır: Tek bir alt öğe (LINQ to XML) alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md). Tarafından döndürülen öğe değerlerini almak için atamalar da kullandığı `M:System.Xml.Linq.XElement.Element` yöntemi.  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Projeksiyonlar ve Dönüşümler (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
