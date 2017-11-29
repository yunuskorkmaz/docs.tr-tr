---
title: "Nasıl yapılır: Proje yeni türü (LINQ-XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7d3deb826bdccdc2a24db84c006fe317a2321442
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Nasıl yapılır: Proje yeni türü (LINQ-XML) (C#)
Bu bölümdeki diğer örnekler, sonuç olarak döndüren sorgular göstermiştir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> , `string`, ve <xref:System.Collections.Generic.IEnumerable%601> , `int`. Bu ortak sonuç türleri olan, ancak her senaryo için uygun değildir. Çoğu durumda döndürülecek sorgularınızı isteyeceksiniz bir <xref:System.Collections.Generic.IEnumerable%601> başka bir tür.  
  
## <a name="example"></a>Örnek  
 Bu örnek nesneleri örneği gösterilmektedir `select` yan tümcesi. Kod ilk bir oluşturucuya sahip yeni bir sınıf tanımlar ve ardından değiştirir `select` deyimi ifade yeni sınıfının yeni bir örneğini olmasını sağlayın.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: tipik satın alma siparişi (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
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
  
 Bu örnekte `M:System.Xml.Linq.XElement.Element` konu başlığı altında tanıtılan yöntemi [nasıl yapılır: tek bir alt öğe (LINQ-XML) alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md). Tarafından döndürülen öğelerinin değerlerini almak için atamalar da kullandığı `M:System.Xml.Linq.XElement.Element` yöntemi.  
  
 Bu örnek şu çıkışı üretir:  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Projeksiyonlar ve dönüştürmeler (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
