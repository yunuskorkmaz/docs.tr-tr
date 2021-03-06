---
title: 'Son değişiklik: WinForms nesnelerine yerel koddan erişilemiyor'
description: .NET 5 ' teki son değişiklik hakkında bilgi edinmek için Windows Forms nesneleri yerel koddan artık erişilebilir değil.
ms.date: 01/29/2021
ms.openlocfilehash: 823d37cb8115b8669b254878325a350809393e79
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256106"
---
# <a name="native-code-cant-access-windows-forms-objects"></a>Yerel kod Windows Forms nesnelere erişemiyor

.NET 5 ' ten başlayarak, artık Windows Forms nesneleri yerel koddan erişemezsiniz.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, bazı Windows Forms türler COM birlikte çalışabilirliğine görünür olarak tasarlanmıştı ve bu nedenle yerel kod tarafından erişilebilirdir. .NET 5 ' den başlayarak, COM birlikte çalışabilirliğine veya yerel koda erişilebilen Windows Forms API 'SI görünmez. .NET çalışma zamanı artık kutudan çıkan özel tür kitaplıkları oluşturmayı desteklememektedir. Ayrıca, .NET çalışma zamanı .NET Framework için tür kitaplığına bağlı olamaz (Bu, .NET Framework olduğu gibi sınıfların şeklinin sürdürülmesi gerekir).

## <a name="reason-for-change"></a>Değişiklik nedeni

- `ComVisible(true)`Tür kitaplığı (tlb dosyası) oluşturma ve arama için kullanılan Numaralandırmalardan kaldırma: .NET Core tarafından sunulan bir WINFORMS tlb olmadığından, bu özniteliği tutma konusunda bir değer yoktur.
- Sınıflardan kaldırma `ComVisible(true)` `AccessibleObject` : sınıflar CoCreateable değildir (parametresiz oluşturucusu yoktur) ve zaten var olan BIR örneği com 'a göstermek bu özniteliği gerektirmez.
- `ComVisible(true)` `Control` Ve `Component` sınıflarının kaldırılması: Bu, ÖRNEĞIN VB6 veya MFC gıbı WinForms denetimlerinin OLE/ActiveX aracılığıyla barındırılmasına izin vermek için kullanılmıştır. Ancak, bu, artık sağlanmamış olan WinForms için bir TLB gerektirir ve ayrıca, aynı zamanda kutudan çıkar. Genellikle, WinForms denetimlerinin COM tabanlı barındırmasına yönelik bakım yoktu, bu nedenle destek, desteklenmeyen bir durumda bırakmak yerine kaldırılmıştır.
- `ClassInterface`Denetimlerden özniteliklerin kaldırılması: OLE/ActiveX aracılığıyla barındırma desteklenmiyorsa, bu özniteliklerin artık gerekli değildir. Bunlar, nesnelerin hala COM 'a açık olduğu ve özniteliğin ilgili olabileceği diğer yerlerde tutulur.
- ' Nin `ComVisible(true)` kaldırılması `EventArgs` , büyük olasılıkla OLE/ActiveX barındırma ile kullanılmıştı ve artık desteklenmiyordur. Bunlar CoCreateable değildir, bu nedenle özniteliğin amacı yoktur. Ayrıca, bir TLB sağlamaya gerek kalmadan mevcut örnekleri göstermek hiçbir fikir vermez.
- `ComVisible(true)`Temsilcilerden kaldırma: amaç bilinmiyor, ancak WinForms denetimlerinin ActiveX barındırılması artık desteklenmediğinden, herhangi bir kullanışsız olma olasılığı düşüktür.
- `ComVisible(true)`Genel olmayan bazı koddan kaldırma: tek potansiyel tüketici yeni Visual Studio Tasarımcısı olacaktır, ancak GUID belirtilmeden, yine de gerekli değildir.
- `ComVisible(true)`Bazı rastgele Genel tasarımcı sınıflarından kaldırma: eski Visual Studio Tasarımcısı bu sınıflarla konuşmak IÇIN com birlikte çalışabilirliği kullanıyor olabilir. Ancak, eski tasarımcı .NET Core 'u desteklemez, bu nedenle çok sayıda kişi bu şekilde olmalıdır `ComVisible` .
- `IWin32Window` .NET Framework ' de tanımlanan aynı GUID ' de tanımlanmış, bu da tehlikeli sonuçlara sahip. .NET Framework birlikte çalışabilirliğine ihtiyacınız varsa kullanın `ComImport` .
- Yönetilen WinForms `IDataObject` yapıldı `ComVisible` . Bu gerekli değildir, `ComImport` com birlikte çalışma için ayrı bir arabirim bildirimi vardır `IDataObject` . `IDataObject` `ComVisible` Hiçbir tlb sağlanmadığından ve sıralama her zaman başarısız olacağı için, yönetilmek için bir karşı üretken olma. Ayrıca, GUID belirtilmemiş ve .NET Framework farklıydı, bu nedenle belgelenmemiş bir IID 'yi kaldırma işlemi müşterileri olumsuz etkileyecek.
- Kaldırma `ComVisible(false)` : Bunlar rastgele rastgele konumlara yerleştirilir ve varsayılan olarak SıNıFLARı com birlikte çalışabilirliğine sunmadığından gereksizdir.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 5.0

## <a name="recommended-action"></a>Önerilen eylem

Aşağıdaki örnek .NET Framework ve .NET Core 3,1 ' de çalışmaktadır. Bu örnek, JavaScript 'In yansıma aracılığıyla form alt sınıfına geri çağırmasını sağlayan .NET Framework türü kitaplığına bağımlıdır.

```cs
[PermissionSet(SecurityAction.Demand, Name="FullTrust")]
[System.Runtime.InteropServices.ComVisibleAttribute(true)]
public class Form1 : Form
{
    private WebBrowser webBrowser1 = new WebBrowser();

    protected override void OnLoad(EventArgs e)
    {
        webBrowser1.AllowWebBrowserDrop = false;
        webBrowser1.IsWebBrowserContextMenuEnabled = false;
        webBrowser1.WebBrowserShortcutsEnabled = false;
        webBrowser1.ObjectForScripting = this;

        webBrowser1.DocumentText =
            "<html><body><button " +
            "onclick=\"window.external.Test('called from script code')\">" +
            "call client code from script code</button>" +
            "</body></html>";
    }

    public void Test(String message)
    {
        MessageBox.Show(message, "client code");
    }
}
```

.NET 5 ve sonraki sürümlerde örneğin çalışması için iki olası yol vardır:

- `ObjectForScripting`' I destekleyen Kullanıcı tarafından belirtilen bir nesne `IDispatch` (varsayılan olarak, proje düzeyinde değiştirilmedikleri takdirde, varsayılan olarak uygulanır) tanıtın.

  ```cs
  public class MyScriptObject
  {
      private Form1 _form;

      public MyScriptObject(Form1 form)
      {
          _form = form;
      }

      public void Test(string message)
      {
          MessageBox.Show(message, "client code");
      }
  }

  public partial class Form1 : Form
  {
      protected override void OnLoad(EventArgs e)
      {
          ...

          // Works correctly.
          webBrowser1.ObjectForScripting = new MyScriptObject(this);

          ...
      }
  }
  ```

- Sergileme yöntemleriyle bir arabirim bildirin.

  ```cs
  public interface IForm1
  {
      void Test(string message);
  }

  [ComDefaultInterface(typeof(IForm1))]
  public partial class Form1 : Form, IForm1
  {
      protected override void OnLoad(EventArgs e)
      {
          ...

          // Works correctly.
          webBrowser1.ObjectForScripting = this;

          ...
      }
  }
  ```

## <a name="affected-apis"></a>Etkilenen API’ler

Tüm Windows Forms API 'Leri.

<!--

### Category

- Windows Forms

-->
