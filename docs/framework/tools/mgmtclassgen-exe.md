---
title: Mgmtclassgen.exe (Yönetim Türü Kesin Belirlenmiş Sınıf Oluşturucu)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e018d8c83165b3e025ad4db7f3d59b6ba58b72a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616088"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a>Mgmtclassgen.exe (Yönetim Türü Kesin Belirlenmiş Sınıf Oluşturucu)
Yönetim Kesin Belirlenmiş Sınıf Üreticisi aracı, belirtilen bir Windows Yönetim Araçları (WMI) sınıfı için erken bağlı yönetilen bir sınıfı hızlı bir şekilde üretmenize olanak tanır. Oluşturulan sınıf, WMI sınıfının bir örneğine erişmek için yazmanız gereken kodu basitleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
mgmtclassgen   
WMIClass [options]   
```  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*Wmıclass*|Kendisi için erken bağlı yönetilen bir sınıf oluşturulacak Windows Yönetim Araçları sınıfı.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/l***dil*|Erken bağlı yönetilen sınıfın oluşturulacağı dili belirtir. Belirtebileceğiniz **CS** (C#; varsayılan), **VB** (Visual Basic) **MC** (C++) veya **JS** (JScript) dil bağımsız değişken olarak.|  
|**/m***makine*|WMI sınıfının bulunduğu, bağlanılacak bilgisayarı belirtir. Varsayılan, yerel bilgisayardır.|  
|**/n***yolu*|WMI sınıfını içeren WMI ad alanına giden yolu belirtir. Bu seçeneği belirtmezseniz, araç için kod oluşturur. *Wmıclass* varsayılan **root\cımv2** ad alanı.|  
|**/o***classnamespace*|Yönetilen kod sınıfının içinde üretileceği .NET ad alanını belirtir. Bu seçeneği belirtmezseniz, araç ad alanını WMI ad alanını ve şema önekini kullanarak üretir. Şema öneki, sınıf adının alt çizgi karakterinden önce gelen parçasıdır. Örneğin, **Win32_OperatingSystem** sınıfını **root\cımv2** ad oluşturma aracı sınıfında **kök. CIMV2. Win32**.|  
|**/p***dosya yolu*|Üretilen kodun içinde kaydedileceği dosyanın yolunu belirtir. Bu seçeneği belirtmezseniz, araç dosyayı geçerli dizinde oluşturur. Oluşturur sınıfını kullanarak dosya ve sınıf adları *Wmıclass* bağımsız değişken. Sınıfın ve dosyanın adı olan adı ile aynı *Wmıclass.* Varsa *Wmıclass* bir alt çizgi karakteri içeren sınıf adının alt çizgi karakterinden parçası Aracı'nı kullanır. Örneğin, varsa *Wmıclass* addır biçiminde **Win32_LogicalDisk**, üretilen sınıf ve dosya "logicaldisk" olarak adlandırılır. Bir dosya zaten varsa, araç varolan dosyanın üzerine yazar.|  
|**/pw***parola*|Tarafından belirtilen bir bilgisayarda oturum açarken kullanılacak parolayı belirtir **/m** seçeneği.|  
|**/u***kullanıcı adı*|Tarafından belirtilen bir bilgisayarda oturum açarken kullanılacak kullanıcı adını belirtir **/m** seçeneği.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 MgmtClassGen.exe kullanan <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> yöntemi. Bu nedenle, C#, Visual Basic ve JScript'ten başka yönetilen dillerde kod üretmek için, herhangi bir özel kod sağlayıcısını kullanabilirsiniz.  
  
 Üretilen sınıfların, kendisi için üretildikleri şemaya bağlı olduklarını unutmayın. Arka plandaki şema değişirse, şemada yapılan değişiklikleri yansıtmasını isterseniz, sınıfı yeniden oluşturmanız gerekir.  
  
 Aşağıdaki tabloda, WMI Ortak Bilgi Modeli (CIM) türlerinin üretilmiş bir sınıftaki veri türleriyle nasıl eşleştiği gösterilmektedir:  
  
|CIM türü|Oluşturulan sınıf içinde veri türü|  
|--------------|--------------------------------------|  
|CIM_SINT8|**SByte**|  
|CIM_UINT8|**Bayt**|  
|CIM_SINT16|**Int16**|  
|CIM_UINT16|**UInt16**|  
|CIM_SINT32|**Int32**|  
|SIM_UINT32|**UInt32**|  
|CIM_SINT64|**Int64**|  
|CIM_UINT64|**UInt64**|  
|CIM_REAL32|**Tek**|  
|CIM_REAL64|**çift**|  
|CIM_BOOLEAN|**Boole değeri**|  
|CIM_String|**Dize**|  
|CIM_DATETIME|**DateTime** veya **TimeSpan**|  
|CIM_REFERENCE|**ManagementPath**|  
|CIM_CHAR16|**Char**|  
|CIM_OBJECT|**ManagementBaseObject**|  
|CIM_IUNKNOWN|**Nesne**|  
|CIM_ARRAY|Yukarıda sözü edilen nesnelerin dizisi|  
  
 Bir WMI sınıfı oluşturduğunuzda, aşağıdaki davranışlara dikkat edin:  
  
- Standart bir genel özelliğin veya yöntemin, varolan bir özellikle veya yöntemle aynı ada sahip olması olanaklıdır. Bu durumda, araç, adlandırma çakışmalarından kaçınmak için, oluşturulan sınıfta özellik veya yöntemin adını değiştirir.  
  
- Oluşturulan bir sınıftaki bir özellik veya yöntemin adının hedef programlama dilinde bir anahtar sözcük olması olanaklıdır. Bu durumda, araç, adlandırma çakışmalarından kaçınmak için, oluşturulan sınıfta özellik veya yöntemin adını değiştirir.  
  
- WMI'da, niteleyiciler bir sınıfı, örneği, özelliği veya yöntemi tanımlamak için bilgi içeren değiştiricilerdir. WMI kullanan standart niteleyiciler gibi **okuma**, **yazma**, ve **anahtar** oluşturulan bir sınıftaki bir özelliği tanımlamak için. Örneğin, değiştirilen bir özellik bir **okuma** niteleyicisi olan bir özellik tanımlanmıştır **alma** oluşturulan sınıftaki erişimcisi. İşaretlenen bir özelliğin çünkü **okuma** niteleyicisi salt okunur olacak şekilde tasarlanmıştır bir **ayarlamak** erişimcisi tanımlanmaz.  
  
- Sayısal bir özellik tarafından değiştirilebilir **değerleri** ve **ValueMaps** niteleyicileri özelliği yalnızca ayarlanabilir belirtmek için izin verilen değerler belirtildi. Bir numaralandırma ile oluşturulan **değerleri** ve **ValueMaps** ve özellik numaralandırmayla eşleştirilir.  
  
- WMI, yalnızca bir örneği olabilecek bir sınıf tanımlamak için singleton terimini kullanır. Bu nedenle, tek bir singleton sınıfı için varsayılan oluşturucu, sınıfı sınıfın tek örneğine hazırlar.  
  
- Bir WMI sınıfının, nesne olan özellikleri olabilir. Bu tür WMI sınıfı için kesin olarak belirlenmiş bir sınıf ürettiğinizde, gömülü nesne özellikleri türleri için kesin olarak belirlenmiş türler oluşturmayı düşünmelisiniz. Bu, gömülü nesnelere kesin olarak belirlenmiş bir şekilde erişmenize olanak tanır. Üretilen kodun gömülü nesnenin türünü algılayamayacağını unutmayın. Bu durumda, sorunu size bildirmek için, üretilen kodda bir açıklama oluşturulur. Sonra, özelliği üretilen diğer sınıfa yazmak için, üretilen kodu değiştirebilirsiniz.  
  
- WMI'da, CIM_DATETIME veri türünün veri değeri belirli bir tarih ve saati veya bir zaman aralığını gösterebilir. Veri değeri bir tarih ve saat gösterirse, oluşturulan sınıftaki veri türü olan **DateTime**. Veri değeri bir zaman aralığını gösterirse oluşturulan sınıftaki veri türü olan **TimeSpan**.  
  
 Alternatif olarak, Visual Studio .NET'te Sunucu Gezgini Yönetim Uzantısı'nı kullanarak, kesin olarak belirlenmiş bir sınıf oluşturabilirsiniz.  
  
 WMI hakkında daha fazla bilgi için bkz. **Windows Yönetim Araçları'nı** Platform SDK belgelerinde konu.  
  
## <a name="examples"></a>Örnekler  
 Yönetilen sınıfta aşağıdaki komutu oluşturur C# için kod **Win32_LogicalDisk** WMI sınıfının **root\cımv2** ad alanı. Aracı yönetilen sınıf içinde c:\disk.cs konumundaki kaynak dosyasına yazar. **kök. CIMV2. Win32** ad alanı.  
  
```  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 Aşağıdaki kod örneği, oluşturulan bir sınıfın programsal olarak nasıl kullanılacağını göstermektedir. İlk olarak, sınıfın bir örneği numaralandırılır ve yol yazdırılır. Ardından, başlatılacak oluşturulan sınıfın bir örneği bir WMI örneğiyle oluşturulur. `Process` için oluşturulan sınıftır **Win32_Process** ve `LogicalDisk` için oluşturulan sınıftır **Win32_LogicalDisk** içinde **root\cımv2** ad alanı.  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App     
   Public Shared Sub Main()        
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process     
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [Araçlar](../../../docs/framework/tools/index.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
