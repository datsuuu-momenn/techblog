## 1. 図1 – 基本的な VSCode SSH 接続構造（draw.io 用）

### 図の構成

- **矩形(青)**：VSCode（ローカルPC）
    
- **矩形(緑)**：リモート開発サーバ
    
- **矢印**：SSH（暗号化通信）
    
- **説明テキスト**：通信経路
    

### draw.io XML（貼り付け用）

```xml
<mxfile host="app.diagrams.net">
  <diagram name="VSCode SSH Basic" id="basic1">
    <mxGraphModel>
      <root>
        <mxCell id="0" />
        <mxCell id="1" parent="0" />
        <!-- VSCode -->
        <mxCell id="2" value="VSCode (Local PC)" style="rounded=0;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
          <mxGeometry x="40" y="60" width="160" height="60" as="geometry" />
        </mxCell>
        <!-- SSH arrow -->
        <mxCell id="3" style="edgeStyle=elbowEdgeStyle;endArrow=block;html=1;strokeColor=#000000;" edge="1" parent="1" source="2" target="4">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        <!-- Server -->
        <mxCell id="4" value="Remote Dev Server" style="rounded=0;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
          <mxGeometry x="300" y="60" width="160" height="60" as="geometry" />
        </mxCell>
        <!-- Label SSH -->
        <mxCell id="5" value="SSH (Encrypted)" style="text;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;" vertex="1" parent="1">
          <mxGeometry x="220" y="40" width="120" height="20" as="geometry" />
        </mxCell>
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## 2. 図2 – 踏み台サーバ経由（draw.io 用）

### 図の構成

- **矩形(青)**：VSCode（ローカルPC）
    
- **矩形(オレンジ)**：Bastion / 踏み台サーバ
    
- **矩形(緑)**：リモート開発サーバ
    
- **矢印**：SSH（暗号化通信）
    

### draw.io XML

```xml
<mxfile host="app.diagrams.net">
  <diagram name="VSCode SSH Bastion" id="bastion1">
    <mxGraphModel>
      <root>
        <mxCell id="0" />
        <mxCell id="1" parent="0" />
        <!-- VSCode -->
        <mxCell id="2" value="VSCode (Local PC)" style="rounded=0;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
          <mxGeometry x="40" y="60" width="160" height="60" as="geometry" />
        </mxCell>
        <!-- SSH to Bastion -->
        <mxCell id="3" style="edgeStyle=elbowEdgeStyle;endArrow=block;html=1;strokeColor=#000000;" edge="1" parent="1" source="2" target="4">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        <!-- Bastion -->
        <mxCell id="4" value="Bastion / Jump Host" style="rounded=0;fillColor=#ffe6cc;strokeColor=#d79b00;" vertex="1" parent="1">
          <mxGeometry x="260" y="60" width="160" height="60" as="geometry" />
        </mxCell>
        <!-- SSH to Remote -->
        <mxCell id="5" style="edgeStyle=elbowEdgeStyle;endArrow=block;html=1;strokeColor=#000000;" edge="1" parent="1" source="4" target="6">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        <!-- Remote Dev Server -->
        <mxCell id="6" value="Remote Dev Server" style="rounded=0;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
          <mxGeometry x="480" y="60" width="160" height="60" as="geometry" />
        </mxCell>
        <!-- Labels -->
        <mxCell id="7" value="SSH (Encrypted)" style="text;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;" vertex="1" parent="1">
          <mxGeometry x="120" y="40" width="120" height="20" as="geometry" />
        </mxCell>
        <mxCell id="8" value="SSH (Encrypted)" style="text;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;" vertex="1" parent="1">
          <mxGeometry x="360" y="40" width="120" height="20" as="geometry" />
        </mxCell>
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## 使い方

1. [draw.io (diagrams.net)](https://app.diagrams.net/) を開く
    
2. **「ファイル」→「インポート」** を選択
    
3. 上記 XML を貼り付け or アップロード
    
4. 色やフォントは好みに調整可能
