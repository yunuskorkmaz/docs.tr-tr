---
title: Bir XDocument sorgulama ve XElement sorgulama (C#)
description: Bir XDocument sorgulama ve bir XElement sorgulama arasındaki farklar hakkında bilgi edinin. Bu farklılıkları gösteren kod örneklerini gözden geçirin.
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 0c81768f06148308a639f96f4041e464b24edd33
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300325"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a>Bir XDocument sorgulama ve XElement sorgulama (C#)
Aracılığıyla bir belge yüklediğinizde <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , ile yükleme yaparken sorguları biraz farklı yazacağınız fark edeceksiniz <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> .  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>XDocument. Load ve XElement. Load karşılaştırması  
 Bir XML belgesini <xref:System.Xml.Linq.XElement> aracılığıyla yüklediğinizde <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> , <xref:System.Xml.Linq.XElement> XML ağacının kök öğesi yüklenen belgenin kök öğesini içerir. Ancak, bir ile aynı XML belgesini yüklediğinizde <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , ağacın kökü bir <xref:System.Xml.Linq.XDocument> düğümdür ve yüklenen belgenin kök öğesi, öğesinin izin verilen alt <xref:System.Xml.Linq.XElement> düğümüdür <xref:System.Xml.Linq.XDocument> . [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Eksenler kök düğüme göre çalışır.  
  
 Bu ilk örnek kullanarak bir XML ağacı yükler <xref:System.Xml.Linq.XElement.Load%2A> . Daha sonra ağacın kök öğelerinin alt öğelerini sorgular.  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Beklendiği gibi, bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 Aşağıdaki örnek, XML ağacının bir yerine bir olarak yüklendiği özel durum ile, yukarıdaki bir ile aynıdır <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> .  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Aynı sorgunun `Root` üç alt düğüm yerine bir düğümü döndürtiğine dikkat edin.  
  
 Bu ile ilgilenmeye yönelik bir yaklaşım <xref:System.Xml.Linq.XDocument.Root%2A> , aşağıdaki gibi, eksen yöntemlerine erişmeden önce özelliğini kullanmaktır:  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Bu sorgu artık, içinde kök ağaçtaki sorgu ile aynı şekilde gerçekleştirilir <xref:System.Xml.Linq.XElement> . Örnek aşağıdaki çıktıyı üretir:  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  