---
title: 'Nasıl yapılır: bir dosyanın derleme (Visual Basic) olup olmadığını belirleme'
ms.date: 07/20/2015
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
ms.openlocfilehash: 84d45cea4a2557350edacd5f05b12c8ffcac4df8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643255"
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
