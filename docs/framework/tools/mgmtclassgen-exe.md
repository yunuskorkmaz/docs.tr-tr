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
ms.openlocfilehash: 5e39670fbb40acb999a243ac86683219f3c89e4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180372"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a>Mgmtclassgen.exe (Yönetim Türü Kesin Belirlenmiş Sınıf Oluşturucu)
Yönetim Kesin Belirlenmiş Sınıf Üreticisi aracı, belirtilen bir Windows Yönetim Araçları (WMI) sınıfı için erken bağlı yönetilen bir sınıfı hızlı bir şekilde üretmenize olanak tanır. Oluşturulan sınıf, WMI sınıfının bir örneğine erişmek için yazmanız gereken kodu basitleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
mgmtclassgen
WMIClass [options]
```  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*WMIClass*|Kendisi için erken bağlı yönetilen bir sınıf oluşturulacak Windows Yönetim Araçları sınıfı.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/l**  *dili*|Erken bağlı yönetilen sınıfın oluşturulacağı dili belirtir. Dil bağımsız değişkeni olarak **CS** (C#; varsayılan), **VB** (Visual Basic), **MC** (C++) veya **JS (JScript)** belirtebilirsiniz.|  
|**/m**  *makinesi*|WMI sınıfının bulunduğu, bağlanılacak bilgisayarı belirtir. Varsayılan, yerel bilgisayardır.|  
|**/n**  *yolu*|WMI sınıfını içeren WMI ad alanına giden yolu belirtir. Bu seçeneği belirtmezseniz, araç varsayılan **Root\cimv2** ad alanında *WMIClass* için kod oluşturur.|  
|**/o**  *sınıfnamealanı*|Yönetilen kod sınıfının içinde üretileceği .NET ad alanını belirtir. Bu seçeneği belirtmezseniz, araç ad alanını WMI ad alanını ve şema önekini kullanarak üretir. Şema öneki, sınıf adının alt çizgi karakterinden önce gelen parçasıdır. Örneğin, **Root\cimv2** ad alanındaki **Win32_OperatingSystem** sınıfı için araç ROOT'da sınıf **oluşturur. CIMV2. Win32**.|  
|**/p**  *filepath*|Üretilen kodun içinde kaydedileceği dosyanın yolunu belirtir. Bu seçeneği belirtmezseniz, araç dosyayı geçerli dizinde oluşturur. *WMIClass* bağımsız değişkenini kullanarak sınıfı oluşturduğu sınıf ve dosyayı adlandırır. Sınıfın ve dosyanın adı *WMIClass'ın* adı ile aynıdır. *WMIClass* bir alt alt karakter içeriyorsa, araç alt çiziyi izleyen sınıf adının bölümünü kullanır. Örneğin, *WMIClass* adı **Win32_LogicalDisk**biçimindeyse, oluşturulan sınıf ve dosya "logicaldisk" olarak adlandırılır. Bir dosya zaten varsa, araç varolan dosyanın üzerine yazar.|  
|**/pw**  *şifresi*|**/m** seçeneği tarafından belirtilen bir bilgisayarda oturum açarken kullanılacak parolayı belirtir.|  
|**/u**  *kullanıcı adı*|**/m** seçeneği tarafından belirtilen bir bilgisayarda oturum açarken kullanılacak kullanıcı adını belirtir.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Mgmtclassgen.exe yöntemikullanır. <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> Bu nedenle, C#, Visual Basic ve JScript'ten başka yönetilen dillerde kod üretmek için, herhangi bir özel kod sağlayıcısını kullanabilirsiniz.  
  
 Üretilen sınıfların, kendisi için üretildikleri şemaya bağlı olduklarını unutmayın. Arka plandaki şema değişirse, şemada yapılan değişiklikleri yansıtmasını isterseniz, sınıfı yeniden oluşturmanız gerekir.  
  
 Aşağıdaki tabloda, WMI Ortak Bilgi Modeli (CIM) türlerinin üretilmiş bir sınıftaki veri türleriyle nasıl eşleştiği gösterilmektedir:  
  
|CIM türü|Oluşturulan sınıf içinde veri türü|  
|--------------|--------------------------------------|  
|CIM_SINT8|**Sbyte**|  
|CIM_UINT8|**Bayt**|  
|CIM_SINT16|**Int16**|  
|CIM_UINT16|**UInt16**|  
|CIM_SINT32|**Int32**|  
|SIM_UINT32|**UInt32**|  
|CIM_SINT64|**Int64**|  
|CIM_UINT64|**UInt64**|  
|CIM_REAL32|**Tek**|  
|CIM_REAL64|**Çift**|  
|CIM_BOOLEAN|**Boole**|  
|CIM_String|**Dize**|  
|CIM_DATETIME|**DateTime** veya **TimeSpan**|  
|CIM_REFERENCE|**Managementpath**|  
|CIM_CHAR16|**Char**|  
|CIM_OBJECT|**Managementbaseobject**|  
|CIM_IUNKNOWN|**Nesne**|  
|CIM_ARRAY|Yukarıda sözü edilen nesnelerin dizisi|  
  
 Bir WMI sınıfı oluşturduğunuzda, aşağıdaki davranışlara dikkat edin:  
  
- Standart bir genel özelliğin veya yöntemin, varolan bir özellikle veya yöntemle aynı ada sahip olması olanaklıdır. Bu durumda, araç, adlandırma çakışmalarından kaçınmak için, oluşturulan sınıfta özellik veya yöntemin adını değiştirir.  
  
- Oluşturulan bir sınıftaki bir özellik veya yöntemin adının hedef programlama dilinde bir anahtar sözcük olması olanaklıdır. Bu durumda, araç, adlandırma çakışmalarından kaçınmak için, oluşturulan sınıfta özellik veya yöntemin adını değiştirir.  
  
- WMI'da, niteleyiciler bir sınıfı, örneği, özelliği veya yöntemi tanımlamak için bilgi içeren değiştiricilerdir. WMI, oluşturulan bir sınıftaki bir özelliği tanımlamak için **Oku,** **Yaz**ve **Anahtar** gibi standart niteleyicileri kullanır. Örneğin, **Read** niteleyicisi ile değiştirilen bir özellik yalnızca oluşturulan sınıftabir özellik **erişime sahip** bir özellik ile tanımlanır. **Read** niteleyicisiyle işaretlenmiş bir özellik salt okunur olması amaçlandığı **için, ayarlanmış** bir erişimci tanımlanmaz.  
  
- Sayısal bir **özellik, değer** ve **Değer Haritaları** niteleyicileri tarafından, özelliğin yalnızca izin verilen değerlere ayarlanabileceğini belirtmek için değiştirilebilir. Bu **Değerler** ve **ValueMaps** ile numaralandırma oluşturulur ve özellik numaralandırmaya eşlenir.  
  
- WMI, yalnızca bir örneği olabilecek bir sınıf tanımlamak için singleton terimini kullanır. Bu nedenle, tekton sınıfının parametresiz oluşturucusu sınıfı sınıfın tek örneğine alacaktır.  
  
- Bir WMI sınıfının, nesne olan özellikleri olabilir. Bu tür WMI sınıfı için kesin olarak belirlenmiş bir sınıf ürettiğinizde, gömülü nesne özellikleri türleri için kesin olarak belirlenmiş türler oluşturmayı düşünmelisiniz. Bu, gömülü nesnelere kesin olarak belirlenmiş bir şekilde erişmenize olanak tanır. Üretilen kodun gömülü nesnenin türünü algılayamayacağını unutmayın. Bu durumda, sorunu size bildirmek için, üretilen kodda bir açıklama oluşturulur. Sonra, özelliği üretilen diğer sınıfa yazmak için, üretilen kodu değiştirebilirsiniz.  
  
- WMI'da, CIM_DATETIME veri türünün veri değeri belirli bir tarih ve saati veya bir zaman aralığını gösterebilir. Veri değeri bir tarih ve saati temsil ediyorsa, oluşturulan sınıftaki veri türü **DateTime'dır.** Veri değeri bir zaman aralığını temsil ediyorsa, oluşturulan sınıftaki veri türü **TimeSpan'dır.**  
  
 Alternatif olarak, Visual Studio .NET'te Sunucu Gezgini Yönetim Uzantısı'nı kullanarak, kesin olarak belirlenmiş bir sınıf oluşturabilirsiniz.  
  
 WMI hakkında daha fazla bilgi için Platform SDK belgelerinde **Windows Yönetimi Enstrümantasyon** konusuna bakın.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, **Root\cimv2** ad alanında **wmi** sınıfı Win32_LogicalDisk için C# kodunda yönetilen bir sınıf oluşturur. Araç, yönetilen sınıfı ROOT'daki c:\disk.cs adresindeki kaynak dosyaya **yazar. CIMV2. Win32** ad alanı.  
  
```console  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 Aşağıdaki kod örneği, oluşturulan bir sınıfın programsal olarak nasıl kullanılacağını göstermektedir. İlk olarak, sınıfın bir örneği numaralandırılır ve yol yazdırılır. Ardından, başlatılacak oluşturulan sınıfın bir örneği bir WMI örneğiyle oluşturulur. `Process`**Win32_Process** için oluşturulan sınıftır ve `LogicalDisk` **Root\cimv2** ad alanında **Win32_LogicalDisk** için oluşturulan sınıftır.  
  
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
- [Araçlar](index.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
