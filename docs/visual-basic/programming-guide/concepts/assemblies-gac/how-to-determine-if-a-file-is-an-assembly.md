---
title: "Nasıl yapılır: bir dosyanın derleme (Visual Basic) olup olmadığını belirleme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0930b6504306efd7dfaf019e090a6d1212c65657
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a>Nasıl yapılır: bir dosyanın derleme (Visual Basic) olup olmadığını belirleme
Yönetilen ve bir derleme girdi meta verilerinde içerir ve yalnızca, bir dosyanın derleme olup. Derlemeler ve meta veriler hakkında daha fazla bilgi için Ek Yardım konusuna [derleme bildirimi](../../../../framework/app-domains/assembly-manifest.md).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>El ile bir dosyanın derleme olup olmadığını belirleme  
  
1.  Başlat [Ildasm.exe (IL ayrıştırıcı)](https://msdn.microsoft.com/library/f7dy01k1).  
  
2.  Test etmek istediğiniz dosya yükleyin.  
  
3.  Varsa **ILDASM** dosya taşınabilir yürütülebilir (PE) dosyası değil ve ardından bir derleme değil raporlar. Daha fazla bilgi için Ek Yardım konusuna [nasıl yapılır: derleme içeriği görüntüle](../../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Program aracılığıyla bir dosyanın derleme olup olmadığını belirleme  
  
1.  Çağrı <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> yöntemi, test dosyasının adını ve tam dosya yolunu geçirme.  
  
2.  Varsa bir <xref:System.BadImageFormatException> özel durum, dosya bir derleme değil.  
  
## <a name="example"></a>Örnek  
 Bu örnek bir DLL derleme olup olmadığını görmek için sınar.  
  
```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Yöntemi test dosyasını yükler ve bilgileri okuyun sonra yayımlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.AssemblyName>  
 [Programlama Kavramları](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Derlemeler ve Genel Derleme Önbelleği (Visual Basic)](index.md)
